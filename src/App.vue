<template>
  <div
    class="min-h-screen text-slate-100 antialiased selection:bg-cyan-500 selection:text-slate-950"
  >
    <div class="mx-auto max-w-6xl px-4 sm:px-6 lg:px-8 py-6">
      <header
        class="no-print sticky top-4 z-50 mb-8 rounded-2xl border border-slate-800 bg-slate-900/80 p-3 shadow-xl backdrop-blur-md"
      >
        <div class="flex items-center justify-between gap-3">
          <div class="flex items-center gap-3">
            <div
              class="flex h-10 w-10 items-center justify-center rounded-xl bg-gradient-to-tr from-cyan-500 to-blue-600 font-mono text-sm font-bold text-white shadow-lg shadow-cyan-500/20"
            >
              雪源
            </div>
            <div>
              <h1 class="text-base font-bold leading-none text-white">
                胡雪源
              </h1>
              <p class="mt-1 font-mono text-xs text-cyan-400">
                C/C++ 开发工程师
              </p>
            </div>
          </div>

          <nav class="hidden items-center gap-1 text-sm font-medium md:flex">
            <button
              @click="activeTab = 'all'"
              :class="
                activeTab === 'all'
                  ? 'border-cyan-500/30 bg-cyan-500/10 text-cyan-400'
                  : 'text-slate-400 hover:text-slate-200'
              "
              class="rounded-lg border border-transparent px-3 py-1.5 transition"
            >
              全览
            </button>
            <button
              @click="scrollTo('advantage')"
              class="rounded-lg px-3 py-1.5 text-slate-400 transition hover:text-cyan-400"
            >
              核心优势
            </button>
            <button
              @click="scrollTo('experience')"
              class="rounded-lg px-3 py-1.5 text-slate-400 transition hover:text-cyan-400"
            >
              工作经历
            </button>
            <button
              @click="scrollTo('projects')"
              class="rounded-lg px-3 py-1.5 text-slate-400 transition hover:text-cyan-400"
            >
              精选项目
            </button>
            <button
              @click="scrollTo('skills')"
              class="rounded-lg px-3 py-1.5 text-slate-400 transition hover:text-cyan-400"
            >
              技能矩阵
            </button>
          </nav>

          <div class="flex items-center gap-2">
            <button
              @click="copyPhone"
              class="flex items-center gap-1.5 rounded-lg border border-slate-700 bg-slate-800 px-3 py-1.5 text-xs font-medium text-slate-200 transition hover:bg-slate-700"
              title="复制电话"
            >
              <Copy class="h-3.5 w-3.5 text-cyan-400" />
              <span class="hidden sm:inline">{{
                phoneCopied ? "已复制电话" : "18631456816"
              }}</span>
            </button>
            <button
              @click="printResume"
              class="flex items-center gap-1.5 rounded-lg bg-gradient-to-r from-cyan-500 to-blue-600 px-3 py-1.5 text-xs font-semibold text-slate-950 shadow-md shadow-cyan-500/20 transition hover:from-cyan-400 hover:to-blue-500"
            >
              <Printer class="h-3.5 w-3.5" />
              <span>下载简历</span>
            </button>
          </div>
        </div>
      </header>

      <section
        class="glass-card relative mb-8 overflow-hidden rounded-3xl p-6 sm:p-8 print-border-b"
      >
        <div
          class="pointer-events-none absolute -right-10 -top-10 h-64 w-64 rounded-full bg-cyan-500/10 blur-3xl"
        ></div>

        <div
          class="flex flex-col items-center gap-6 md:flex-row md:items-start md:gap-8"
        >
          <div class="group relative">
            <div
              class="relative z-10 h-28 w-28 overflow-hidden rounded-2xl border-2 border-cyan-500/30 bg-slate-900/80 p-1 shadow-2xl sm:h-32 sm:w-32"
            >
              <img
                src=""
                alt="胡雪源"
                class="h-full w-full rounded-xl object-cover grayscale contrast-125 transition duration-500 group-hover:grayscale-0"
              />
            </div>
            <div
              class="absolute inset-0 rounded-2xl bg-gradient-to-r from-cyan-500 to-blue-600 opacity-30 blur transition duration-500 group-hover:opacity-70"
            ></div>
            <span
              class="absolute -bottom-2 -right-2 z-20 flex items-center gap-1 rounded-full border border-slate-900 bg-emerald-500 px-2 py-0.5 text-[10px] font-bold text-slate-950"
            >
              <span class="h-1.5 w-1.5 rounded-full bg-slate-950"></span>
              中共党员
            </span>
          </div>

          <div class="flex-1 space-y-3 text-center md:text-left">
            <div
              class="flex flex-wrap items-center justify-center gap-3 md:justify-start"
            >
              <h1
                class="text-3xl font-extrabold tracking-tight text-white sm:text-4xl"
              >
                胡雪源
              </h1>
              <span
                class="rounded-full border border-cyan-500/30 bg-cyan-500/10 px-3 py-1 text-xs font-medium font-mono text-cyan-400"
              >
                C++ 高级软件工程师
              </span>
            </div>

            <p
              class="max-w-2xl text-sm leading-relaxed text-slate-300 sm:text-base"
            >
              10年硬件接入与客户端开发经验，熟悉
              <span class="font-semibold text-cyan-400"
                >C++、Qt、Linux（信创）、Web</span
              >
              等技术栈。擅长无人机探测与打击平台、地铁 PIS
              信息系统以及高拍仪图像设备系统的全栈搭建与底层协议解析。
            </p>

            <div
              class="grid grid-cols-2 gap-3 pt-2 text-xs font-mono text-slate-300 sm:grid-cols-4"
            >
              <div
                class="flex items-center justify-center gap-2 rounded-lg border border-slate-800 bg-slate-800/40 p-2 md:justify-start"
              >
                <MapPin class="h-4 w-4 text-cyan-400" />
                <span>工作地: 北京</span>
              </div>
              <div
                class="flex items-center justify-center gap-2 rounded-lg border border-slate-800 bg-slate-800/40 p-2 md:justify-start"
              >
                <Phone class="h-4 w-4 text-cyan-400" />
                <a href="tel:18631456816" class="transition hover:text-cyan-400"
                  >18631456816</a
                >
              </div>
              <div
                class="col-span-2 flex items-center justify-center gap-2 rounded-lg border border-slate-800 bg-slate-800/40 p-2 sm:col-span-1 md:justify-start"
              >
                <Mail class="h-4 w-4 text-cyan-400" />
                <a
                  href="mailto:h1256443530@163.com"
                  class="truncate transition hover:text-cyan-400"
                  >h1256443530@163.com</a
                >
              </div>
              <div
                class="flex items-center justify-center gap-2 rounded-lg border border-slate-800 bg-slate-800/40 p-2 md:justify-start"
              >
                <GraduationCap class="h-4 w-4 text-cyan-400" />
                <span>本科 (2016毕业)</span>
              </div>
            </div>
          </div>
        </div>

        <div
          class="mt-8 grid grid-cols-2 gap-4 border-t border-slate-800/80 pt-6 text-center sm:grid-cols-4"
        >
          <div
            class="rounded-xl border border-slate-800/60 bg-slate-900/50 p-3"
          >
            <div class="text-2xl font-bold font-mono text-cyan-400">10+ 年</div>
            <div class="mt-0.5 text-xs text-slate-400">C/C++ 研发经验</div>
          </div>
          <div
            class="rounded-xl border border-slate-800/60 bg-slate-900/50 p-3"
          >
            <div class="text-2xl font-bold font-mono text-blue-400">多领域</div>
            <div class="mt-0.5 text-xs text-slate-400">
              无人机/轨道交通/信创SDK
            </div>
          </div>
          <div
            class="rounded-xl border border-slate-800/60 bg-slate-900/50 p-3"
          >
            <div class="text-2xl font-bold font-mono text-emerald-400">
              全平台
            </div>
            <div class="mt-0.5 text-xs text-slate-400">
              Windows / Linux / ARM嵌入式
            </div>
          </div>
          <div
            class="rounded-xl border border-slate-800/60 bg-slate-900/50 p-3"
          >
            <div class="text-2xl font-bold font-mono text-purple-400">
              全栈协议
            </div>
            <div class="mt-0.5 text-xs text-slate-400">
              TCP/UDP/MQTT/WebSocket
            </div>
          </div>
        </div>
      </section>

      <section id="advantage" class="mb-10">
        <div class="mb-4 flex items-center justify-between">
          <h2 class="flex items-center gap-2 text-xl font-bold text-white">
            <Zap class="h-5 w-5 text-cyan-400" />
            个人核心优势
          </h2>
        </div>

        <div class="grid grid-cols-1 gap-4 md:grid-cols-2">
          <div
            class="glass-card rounded-2xl border border-slate-800/80 p-5 transition hover:border-cyan-500/30"
          >
            <div class="flex items-start gap-3">
              <div
                class="rounded-xl border border-cyan-500/20 bg-cyan-500/10 p-2.5 text-cyan-400"
              >
                <Radar class="h-5 w-5" />
              </div>
              <div>
                <h3 class="text-base font-semibold text-white">
                  硬件设备接入与系统开发
                </h3>
                <p class="mt-1 text-xs leading-relaxed text-slate-400">
                  高拍仪、扫描仪、摄像头、无人机（探测/打击/诱骗）设备及地铁 PIS
                  系统相关硬件设备的深度接入、底层驱动及应用平台全链路开发能力。
                </p>
              </div>
            </div>
          </div>

          <div
            class="glass-card rounded-2xl border border-slate-800/80 p-5 transition hover:border-blue-500/30"
          >
            <div class="flex items-start gap-3">
              <div
                class="rounded-xl border border-blue-500/20 bg-blue-500/10 p-2.5 text-blue-400"
              >
                <Cpu class="h-5 w-5" />
              </div>
              <div>
                <h3 class="text-base font-semibold text-white">
                  跨平台与嵌入式部署
                </h3>
                <p class="mt-1 text-xs leading-relaxed text-slate-400">
                  熟悉 Windows 及 Linux (银河麒麟、中标麒麟等)国产信创
                  环境开发；熟悉交叉编译链，具备在 ARM
                  主板上部署运行高效程序的实战经验。
                </p>
              </div>
            </div>
          </div>

          <div
            class="glass-card rounded-2xl border border-slate-800/80 p-5 transition hover:border-purple-500/30"
          >
            <div class="flex items-start gap-3">
              <div
                class="rounded-xl border border-purple-500/20 bg-purple-500/10 p-2.5 text-purple-400"
              >
                <Map class="h-5 w-5" />
              </div>
              <div>
                <h3 class="text-base font-semibold text-white">
                  客户端与 Web GIS 联合开发
                </h3>
                <p class="mt-1 text-xs leading-relaxed text-slate-400">
                  熟练掌握 Qt 框架进行高性能桌面客户端开发；熟悉 Vue3 +
                  OpenLayers 架构，能高效完成 Web
                  地图交互及复杂地图态势显控系统开发。
                </p>
              </div>
            </div>
          </div>

          <div
            class="glass-card rounded-2xl border border-slate-800/80 p-5 transition hover:border-emerald-500/30"
          >
            <div class="flex items-start gap-3">
              <div
                class="rounded-xl border border-emerald-500/20 bg-emerald-500/10 p-2.5 text-emerald-400"
              >
                <Network class="h-5 w-5" />
              </div>
              <div>
                <h3 class="text-base font-semibold text-white">
                  全协议通信与中间件开发
                </h3>
                <p class="mt-1 text-xs leading-relaxed text-slate-400">
                  深刻理解并熟练运用 TCP、UDP、HTTP、WebSocket、MQTT、串口
                  (Serial) 及 GPIO，具备高并发高可靠性接口软件及上位机开发实践。
                </p>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section id="experience" class="mb-10">
        <div class="mb-6 flex items-center justify-between">
          <h2 class="flex items-center gap-2 text-xl font-bold text-white">
            <Briefcase class="h-5 w-5 text-cyan-400" />
            工作经历
          </h2>
        </div>

        <div
          class="relative ml-4 space-y-8 border-l-2 border-slate-800/80 pl-6"
        >
          <div class="group relative">
            <div
              class="absolute -left-[31px] top-1.5 h-4 w-4 rounded-full border-2 border-cyan-400 bg-slate-900 transition group-hover:scale-125 group-hover:bg-cyan-400"
            ></div>

            <div
              class="glass-card rounded-2xl border border-slate-800 p-5 transition hover:border-cyan-500/30 sm:p-6"
            >
              <div
                class="mb-3 flex flex-col justify-between gap-2 sm:flex-row sm:items-center"
              >
                <div>
                  <h3
                    class="text-lg font-bold text-white transition group-hover:text-cyan-400"
                  >
                    北京博宏科元信息科技有限公司
                  </h3>
                  <p class="font-mono text-sm font-medium text-cyan-400">
                    C/C++ 工程师
                  </p>
                </div>
                <span
                  class="w-fit rounded-full border border-slate-700/50 bg-slate-800/80 px-3 py-1 text-xs font-mono text-slate-400"
                >
                  2023.03 - 至今
                </span>
              </div>

              <ul
                class="list-inside list-disc space-y-2 text-sm leading-relaxed text-slate-300"
              >
                <li>
                  <strong class="text-white">无人机反制与防护：</strong
                  >负责接入无人机探测设备（协议解析、AOA、TDOA、光电、雷达、信标）与反制设备（全向打击、面向打击、导航诱骗、激光），并根据客户需求定制个性化服务。
                </li>
                <li>
                  <strong class="text-white">第三方平台与接口软件开发：</strong
                  >负责项目中通用接口软件的研发，精准对接第三方业务数据平台。
                </li>
                <li>
                  <strong class="text-white">硬件与嵌入式研发：</strong
                  >负责自研设备上位机管控软件开发及设备内部 ARM
                  嵌入式软件的研发。
                </li>
                <li>
                  <strong class="text-white">智慧交通硬件适配：</strong
                  >负责电动自行车发卡软件开发维护，并配合电动自行车违章抓拍一体机设备的研发调试。
                </li>
              </ul>

              <div
                class="mt-4 flex flex-wrap gap-2 border-t border-slate-800/60 pt-3"
              >
                <span
                  class="rounded border border-cyan-800/50 bg-cyan-950/40 px-2.5 py-0.5 font-mono text-[11px] text-cyan-300"
                  >C/C++</span
                >
                <span
                  class="rounded bg-slate-800 px-2.5 py-0.5 font-mono text-[11px] text-slate-300"
                  >Qt</span
                >
                <span
                  class="rounded bg-slate-800 px-2.5 py-0.5 font-mono text-[11px] text-slate-300"
                  >Vue3+OpenLayers</span
                >
                <span
                  class="rounded bg-slate-800 px-2.5 py-0.5 font-mono text-[11px] text-slate-300"
                  >MQTT / WebSocket</span
                >
                <span
                  class="rounded bg-slate-800 px-2.5 py-0.5 font-mono text-[11px] text-slate-300"
                  >嵌入式/GPIO/串口</span
                >
              </div>
            </div>
          </div>

          <div class="group relative">
            <div
              class="absolute -left-[31px] top-1.5 h-4 w-4 rounded-full border-2 border-slate-600 bg-slate-900 transition group-hover:scale-125 group-hover:border-cyan-400"
            ></div>

            <div
              class="glass-card rounded-2xl border border-slate-800 p-5 transition hover:border-cyan-500/30 sm:p-6"
            >
              <div
                class="mb-3 flex flex-col justify-between gap-2 sm:flex-row sm:items-center"
              >
                <div>
                  <h3
                    class="text-lg font-bold text-white transition group-hover:text-cyan-400"
                  >
                    北京金万维科技有限公司
                  </h3>
                  <p class="font-mono text-sm font-medium text-cyan-400">
                    C/C++ 工程师
                  </p>
                </div>
                <span
                  class="w-fit rounded-full border border-slate-700/50 bg-slate-800/80 px-3 py-1 text-xs font-mono text-slate-400"
                >
                  2022.04 - 2023.03
                </span>
              </div>

              <ul
                class="list-inside list-disc space-y-2 text-sm leading-relaxed text-slate-300"
              >
                <li>
                  <strong class="text-white">信创系统外设适配：</strong
                  >负责高拍仪、摄像头以及身份身份证读卡器硬件在国产信创系统中的接入与驱动封装。
                </li>
                <li>
                  <strong class="text-white">云联客户端：</strong
                  >参与云联客户端软件的核心功能模块开发与日常维护升级。
                </li>
              </ul>

              <div
                class="mt-4 flex flex-wrap gap-2 border-t border-slate-800/60 pt-3"
              >
                <span
                  class="rounded bg-slate-800 px-2.5 py-0.5 font-mono text-[11px] text-slate-300"
                  >C++</span
                >
                <span
                  class="rounded bg-slate-800 px-2.5 py-0.5 font-mono text-[11px] text-slate-300"
                  >信创 Linux</span
                >
                <span
                  class="rounded bg-slate-800 px-2.5 py-0.5 font-mono text-[11px] text-slate-300"
                  >摄像头/读卡器</span
                >
                <span
                  class="rounded bg-slate-800 px-2.5 py-0.5 font-mono text-[11px] text-slate-300"
                  >客户端开发</span
                >
              </div>
            </div>
          </div>

          <div class="group relative">
            <div
              class="absolute -left-[31px] top-1.5 h-4 w-4 rounded-full border-2 border-slate-600 bg-slate-900 transition group-hover:scale-125 group-hover:border-cyan-400"
            ></div>

            <div
              class="glass-card rounded-2xl border border-slate-800 p-5 transition hover:border-cyan-500/30 sm:p-6"
            >
              <div
                class="mb-3 flex flex-col justify-between gap-2 sm:flex-row sm:items-center"
              >
                <div>
                  <h3
                    class="text-lg font-bold text-white transition group-hover:text-cyan-400"
                  >
                    北京北大千方科技有限公司
                  </h3>
                  <p class="font-mono text-sm font-medium text-cyan-400">
                    C++ 工程师
                  </p>
                </div>
                <span
                  class="w-fit rounded-full border border-slate-700/50 bg-slate-800/80 px-3 py-1 text-xs font-mono text-slate-400"
                >
                  2019.10 - 2022.04
                </span>
              </div>

              <ul
                class="list-inside list-disc space-y-2 text-sm leading-relaxed text-slate-300"
              >
                <li>
                  <strong class="text-white">轨道交通 PIS 系统：</strong
                  >负责乘客信息系统（PIS）业务在 Windows 与 Linux
                  环境下的核心功能软件开发与迭代维护。
                </li>
                <li>
                  <strong class="text-white">外设接口封装：</strong
                  >深度封装电源控制器、光矩阵、LED
                  显示屏等物理设备的功能操控接口。
                </li>
                <li>
                  <strong class="text-white">统一接入架构：</strong
                  >开发网络接口软件对接数据中心和通号系统数据接口，实现地铁线路全域设备的统一管理与调度。
                </li>
              </ul>

              <div
                class="mt-4 flex flex-wrap gap-2 border-t border-slate-800/60 pt-3"
              >
                <span
                  class="rounded bg-slate-800 px-2.5 py-0.5 font-mono text-[11px] text-slate-300"
                  >C++ / Linux</span
                >
                <span
                  class="rounded bg-slate-800 px-2.5 py-0.5 font-mono text-[11px] text-slate-300"
                  >PIS乘客信息系统</span
                >
                <span
                  class="rounded bg-slate-800 px-2.5 py-0.5 font-mono text-[11px] text-slate-300"
                  >TCP/UDP网络通信</span
                >
                <span
                  class="rounded bg-slate-800 px-2.5 py-0.5 font-mono text-[11px] text-slate-300"
                  >硬件接口封装</span
                >
              </div>
            </div>
          </div>

          <div class="group relative">
            <div
              class="absolute -left-[31px] top-1.5 h-4 w-4 rounded-full border-2 border-slate-600 bg-slate-900 transition group-hover:scale-125 group-hover:border-cyan-400"
            ></div>

            <div
              class="glass-card rounded-2xl border border-slate-800 p-5 transition hover:border-cyan-500/30 sm:p-6"
            >
              <div
                class="mb-3 flex flex-col justify-between gap-2 sm:flex-row sm:items-center"
              >
                <div>
                  <h3
                    class="text-lg font-bold text-white transition group-hover:text-cyan-400"
                  >
                    北京麦哲科技有限公司
                  </h3>
                  <p class="font-mono text-sm font-medium text-cyan-400">
                    C++ 工程师
                  </p>
                </div>
                <span
                  class="w-fit rounded-full border border-slate-700/50 bg-slate-800/80 px-3 py-1 text-xs font-mono text-slate-400"
                >
                  2016.06 - 2019.10
                </span>
              </div>

              <ul
                class="list-inside list-disc space-y-2 text-sm leading-relaxed text-slate-300"
              >
                <li>
                  <strong class="text-white">Windows 平台开发：</strong
                  >负责高拍仪业务在 Windows 环境下的 MFC
                  图形界面应用、动态链接库 (DLL) 及 ActiveX SDK 开发。
                </li>
                <li>
                  <strong class="text-white">Linux 平台开发：</strong
                  >负责高拍仪业务在 Linux 下基于 Qt 的图像界面以及 .so 动态库
                  SDK 开发。
                </li>
                <li>
                  <strong class="text-white">外设集成与 Web 交互：</strong
                  >封装高拍仪扩展模块（身份证读卡器、指纹仪、手写板、人脸识别），并基于
                  WebSocket 协议支持网页端无缝访问本地硬件。
                </li>
              </ul>

              <div
                class="mt-4 flex flex-wrap gap-2 border-t border-slate-800/60 pt-3"
              >
                <span
                  class="rounded bg-slate-800 px-2.5 py-0.5 font-mono text-[11px] text-slate-300"
                  >C++ / MFC / Qt</span
                >
                <span
                  class="rounded bg-slate-800 px-2.5 py-0.5 font-mono text-[11px] text-slate-300"
                  >SDK封装 (DLL/ActiveX/SO)</span
                >
                <span
                  class="rounded bg-slate-800 px-2.5 py-0.5 font-mono text-[11px] text-slate-300"
                  >WebSocket 硬件交互</span
                >
                <span
                  class="rounded bg-slate-800 px-2.5 py-0.5 font-mono text-[11px] text-slate-300"
                  >指纹/人脸识别模块</span
                >
              </div>
            </div>
          </div>
        </div>
      </section>

      <div
        v-if="showUavDefenseImage"
        class="fixed inset-0 z-50 flex items-center justify-center bg-slate-950/80 p-4 backdrop-blur-sm"
        @click="showUavDefenseImage = false"
      >
        <div
          class="relative w-full max-w-5xl rounded-2xl border border-slate-700 bg-slate-900 p-2 shadow-2xl"
          @click.stop
        >
          <button
            type="button"
            @click="showUavDefenseImage = false"
            class="absolute -right-3 -top-3 flex h-8 w-8 items-center justify-center rounded-full border border-slate-700 bg-slate-900 text-lg text-slate-200 transition hover:bg-slate-800"
            aria-label="关闭图片"
          >
            ×
          </button>
          <img
            src="/uavdefense.png"
            alt="无人机反制平台界面放大图"
            class="max-h-[80vh] w-full rounded-xl object-contain"
          />
        </div>
      </div>

      <div
        v-if="showInterfaceImage"
        class="fixed inset-0 z-50 flex items-center justify-center bg-slate-950/80 p-4 backdrop-blur-sm"
        @click="showInterfaceImage = false"
      >
        <div
          class="relative w-full max-w-5xl rounded-2xl border border-slate-700 bg-slate-900 p-2 shadow-2xl"
          @click.stop
        >
          <button
            type="button"
            @click="showInterfaceImage = false"
            class="absolute -right-3 -top-3 flex h-8 w-8 items-center justify-center rounded-full border border-slate-700 bg-slate-900 text-lg text-slate-200 transition hover:bg-slate-800"
            aria-label="关闭图片"
          >
            ×
          </button>
          <img
            src="/interface.png"
            alt="MqttX 调试界面放大图"
            class="max-h-[80vh] w-full rounded-xl object-contain"
          />
        </div>
      </div>

      <div
        v-if="showAutoTestImage"
        class="fixed inset-0 z-50 flex items-center justify-center bg-slate-950/80 p-4 backdrop-blur-sm"
        @click="showAutoTestImage = false"
      >
        <div
          class="relative w-full max-w-5xl rounded-2xl border border-slate-700 bg-slate-900 p-2 shadow-2xl"
          @click.stop
        >
          <button
            type="button"
            @click="showAutoTestImage = false"
            class="absolute -right-3 -top-3 flex h-8 w-8 items-center justify-center rounded-full border border-slate-700 bg-slate-900 text-lg text-slate-200 transition hover:bg-slate-800"
            aria-label="关闭图片"
          >
            ×
          </button>
          <img
            src="/autest.png"
            alt="自动化测试软件放大图"
            class="max-h-[80vh] w-full rounded-xl object-contain"
          />
        </div>
      </div>

      <div
        v-if="showAoaImage"
        class="fixed inset-0 z-50 flex items-center justify-center bg-slate-950/80 p-4 backdrop-blur-sm"
        @click="showAoaImage = false"
      >
        <div
          class="relative w-full max-w-5xl rounded-2xl border border-slate-700 bg-slate-900 p-2 shadow-2xl"
          @click.stop
        >
          <button
            type="button"
            @click="showAoaImage = false"
            class="absolute -right-3 -top-3 flex h-8 w-8 items-center justify-center rounded-full border border-slate-700 bg-slate-900 text-lg text-slate-200 transition hover:bg-slate-800"
            aria-label="关闭图片"
          >
            ×
          </button>
          <img
            src="/Aoa.png"
            alt="AOA放大图"
            class="max-h-[80vh] w-full rounded-xl object-contain"
          />
        </div>
      </div>

      <section id="projects" class="mb-10">
        <div
          class="mb-6 flex flex-col justify-between gap-4 sm:flex-row sm:items-center"
        >
          <div>
            <h2 class="flex items-center gap-2 text-xl font-bold text-white">
              <Layers class="h-5 w-5 text-cyan-400" />
              精选项目经历
            </h2>
            <p class="mt-1 text-xs text-slate-400">
              涵盖无人机、轨道交通、自动化测试及信创 SDK
            </p>
          </div>

          <div
            class="no-print flex items-center gap-1 rounded-xl border border-slate-800 bg-slate-900/80 p-1 text-xs"
          >
            <button
              @click="projectCategory = 'all'"
              :class="
                projectCategory === 'all'
                  ? 'bg-cyan-500 font-bold text-slate-950'
                  : 'text-slate-400 hover:text-white'
              "
              class="rounded-lg px-3 py-1 transition"
            >
              全部
            </button>
            <button
              @click="projectCategory = 'uav'"
              :class="
                projectCategory === 'uav'
                  ? 'bg-cyan-500 font-bold text-slate-950'
                  : 'text-slate-400 hover:text-white'
              "
              class="rounded-lg px-3 py-1 transition"
            >
              无人机系统
            </button>
            <button
              @click="projectCategory = 'hardware'"
              :class="
                projectCategory === 'hardware'
                  ? 'bg-cyan-500 font-bold text-slate-950'
                  : 'text-slate-400 hover:text-white'
              "
              class="rounded-lg px-3 py-1 transition"
            >
              硬件/信创SDK
            </button>
          </div>
        </div>

        <div class="grid grid-cols-1 gap-5 md:grid-cols-2">
          <div
            v-if="projectCategory === 'all' || projectCategory === 'uav'"
            class="glass-card flex flex-col justify-between rounded-2xl border border-slate-800 p-5 transition hover:border-cyan-500/40"
          >
            <div>
              <div class="mb-2 flex items-center justify-between gap-2">
                <h3
                  class="flex items-center gap-2 text-base font-bold text-white"
                >
                  <ShieldAlert class="h-4 w-4 text-cyan-400" />
                  无人机反制平台开发
                </h3>
                <span
                  class="rounded border border-cyan-800 bg-cyan-950/60 px-2 py-0.5 font-mono text-[10px] text-cyan-300"
                  >C++ / Web GIS</span
                >
              </div>
              <p class="mb-4 text-xs leading-relaxed text-slate-300">
                开发和维护无人机反制平台，提供设备集约化管理以及无人机目标动态轨迹显示、危险预警告警功能。
              </p>
              <div
                class="mb-4 overflow-hidden rounded-xl border border-slate-800/80 bg-slate-900/60"
              >
                <button
                  type="button"
                  @click="showUavDefenseImage = true"
                  class="block w-full cursor-zoom-in bg-slate-950/30 text-left"
                >
                  <img
                    src="/uavdefense.png"
                    alt="无人机反制平台界面"
                    class="h-48 w-full object-contain transition duration-300 hover:scale-[1.02]"
                  />
                </button>
              </div>
              <p class="mb-3 text-[11px] leading-relaxed text-cyan-300">
                点击图片可放大查看：该界面展示设备管理、目标态势与告警中心的综合控制面板。
              </p>
              <div
                class="mb-4 space-y-1 rounded-xl border border-slate-800/80 bg-slate-900/60 p-3 text-xs"
              >
                <div class="text-slate-400">
                  <strong class="text-slate-200">核心架构:</strong> 使用 C++ &
                  Qt 框架搭建高性能客户端应用。
                </div>
                <div class="text-slate-400">
                  <strong class="text-slate-200">态势显示:</strong> 运用 Vue3 +
                  OpenLayers
                  构建地图服务，完美实现设备及空域无人机目标的高帧率地图态势展示。
                </div>
              </div>
            </div>
            <div
              class="flex flex-wrap gap-1.5 border-t border-slate-800/60 pt-2"
            >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >C++</span
              >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >Qt</span
              >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >Vue3</span
              >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >OpenLayers</span
              >
            </div>
          </div>

          <div
            v-if="projectCategory === 'all' || projectCategory === 'uav'"
            class="glass-card flex flex-col justify-between rounded-2xl border border-slate-800 p-5 transition hover:border-cyan-500/40"
          >
            <div>
              <div class="mb-2 flex items-center justify-between gap-2">
                <h3
                  class="flex items-center gap-2 text-base font-bold text-white"
                >
                  <Network class="h-4 w-4 text-blue-400" />
                  无人机反制平台接口软件
                </h3>
                <span
                  class="rounded border border-blue-800 bg-blue-950/60 px-2 py-0.5 font-mono text-[10px] text-blue-300"
                  >MQTT / HTTP</span
                >
              </div>
              <p class="mb-4 text-xs leading-relaxed text-slate-300">
                实时上报反制平台中所管理的设备在线状态及搜获无人机目标轨迹数据，并向下提供标准化的设备管控接口。
              </p>
              <div
                class="mb-4 overflow-hidden rounded-xl border border-slate-800/80 bg-slate-900/60"
              >
                <button
                  type="button"
                  @click="showInterfaceImage = true"
                  class="block w-full cursor-zoom-in bg-slate-950/30 text-left"
                >
                  <img
                    src="/interface.png"
                    alt="MqttX 调试界面"
                    class="h-48 w-full object-contain transition duration-300 hover:scale-[1.02]"
                  />
                </button>
              </div>
              <p class="mb-3 text-[11px] leading-relaxed text-cyan-300">
                点击图片可放大查看：该MqttX 调试打印数据。
              </p>
              <div
                class="mb-4 space-y-1 rounded-xl border border-slate-800/80 bg-slate-900/60 p-3 text-xs"
              >
                <div class="text-slate-400">
                  <strong class="text-slate-200">状态上报:</strong> 使用 MQTT
                  高并发协议推送实时轨迹与设备心跳。
                </div>
                <div class="text-slate-400">
                  <strong class="text-slate-200">控制联动:</strong> 使用 HTTP
                  协议提供低时延的打击控制指令下发功能。
                </div>
              </div>
            </div>
            <div
              class="flex flex-wrap gap-1.5 border-t border-slate-800/60 pt-2"
            >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >C++</span
              >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >MQTT 协议</span
              >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >HTTP API</span
              >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >第三方对接</span
              >
            </div>
          </div>

          <div
            v-if="projectCategory === 'all' || projectCategory === 'uav'"
            class="glass-card flex flex-col justify-between rounded-2xl border border-slate-800 p-5 transition hover:border-cyan-500/40"
          >
            <div>
              <div class="mb-2 flex items-center justify-between gap-2">
                <h3
                  class="flex items-center gap-2 text-base font-bold text-white"
                >
                  <Radio class="h-4 w-4 text-emerald-400" />
                  无人机探测和打击设备开发
                </h3>
                <span
                  class="rounded border border-emerald-800 bg-emerald-950/60 px-2 py-0.5 font-mono text-[10px] text-emerald-300"
                  >B/S 架构 / 嵌入式</span
                >
              </div>
              <p class="mb-4 text-xs leading-relaxed text-slate-300">
                开发物理设备内部基于 B/S
                架构的后台管理及通讯程序，使用户能直接通过标准浏览器远程管控设备。
              </p>
              <div
                class="mb-4 overflow-hidden rounded-xl border border-slate-800/80 bg-slate-900/60"
              >
                <button
                  type="button"
                  @click="showAoaImage = true"
                  class="block w-full cursor-zoom-in bg-slate-950/30 text-left"
                >
                  <img
                    src="/Aoa.png"
                    alt="Aoa软件界面"
                    class="h-48 w-full object-contain transition duration-300 hover:scale-[1.02]"
                  />
                </button>
              </div>
              <p class="mb-3 text-[11px] leading-relaxed text-cyan-300">
                点击图片可放大查看：该自动化测试软件界面。
              </p>
              <div
                class="mb-4 space-y-1 rounded-xl border border-slate-800/80 bg-slate-900/60 p-3 text-xs"
              >
                <div class="text-slate-400">
                  <strong class="text-slate-200">WebUI 前端:</strong> 基于 Vue +
                  OpenLayers 搭建直观可视化的地质地图交互界面。
                </div>
                <div class="text-slate-400">
                  <strong class="text-slate-200">后端通信:</strong> 结合 HTTP 与
                  WebSocket 实现低延迟即时推送，底层结合 Serial 串口、GPIO
                  等操纵硬件模块。
                </div>
              </div>
            </div>
            <div
              class="flex flex-wrap gap-1.5 border-t border-slate-800/60 pt-2"
            >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >Vue / OpenLayers</span
              >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >WebSocket</span
              >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >GPIO</span
              >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >串口通信</span
              >
            </div>
          </div>

          <div
            v-if="projectCategory === 'all' || projectCategory === 'hardware'"
            class="glass-card flex flex-col justify-between rounded-2xl border border-slate-800 p-5 transition hover:border-cyan-500/40"
          >
            <div>
              <div class="mb-2 flex items-center justify-between gap-2">
                <h3
                  class="flex items-center gap-2 text-base font-bold text-white"
                >
                  <SlidersHorizontal class="h-4 w-4 text-purple-400" />
                  一体机射频自动化测试软件
                </h3>
                <span
                  class="rounded border border-purple-800 bg-purple-950/60 px-2 py-0.5 font-mono text-[10px] text-purple-300"
                  >C++ / Qt / 硬件控制</span
                >
              </div>
              <p class="mb-4 text-xs leading-relaxed text-slate-300">
                为抓拍/识别一体机设备研制生产线自动化测试程序，实现射频正反向参数的自动化精调与校准。
              </p>
              <div
                class="mb-4 overflow-hidden rounded-xl border border-slate-800/80 bg-slate-900/60"
              >
                <button
                  type="button"
                  @click="showAutoTestImage = true"
                  class="block w-full cursor-zoom-in bg-slate-950/30 text-left"
                >
                  <img
                    src="/autest.png"
                    alt="自动化测试软件界面"
                    class="h-48 w-full object-contain transition duration-300 hover:scale-[1.02]"
                  />
                </button>
              </div>
              <p class="mb-3 text-[11px] leading-relaxed text-cyan-300">
                点击图片可放大查看：该自动化测试软件界面。
              </p>
              <div
                class="mb-4 space-y-1 rounded-xl border border-slate-800/80 bg-slate-900/60 p-3 text-xs"
              >
                <div class="text-slate-400">
                  <strong class="text-slate-200">射频测试:</strong> 使用 C++ &
                  Qt 控制频谱仪测试设备正向频率和功率准确度。
                </div>
                <div class="text-slate-400">
                  <strong class="text-slate-200">信号校准:</strong>
                  驱动信号源完成设备反向接收频率和灵敏度功率的精确自动化校准。
                </div>
              </div>
            </div>
            <div
              class="flex flex-wrap gap-1.5 border-t border-slate-800/60 pt-2"
            >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >C++</span
              >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >Qt 客户端</span
              >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >频谱仪控制</span
              >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >信号源校准</span
              >
            </div>
          </div>

          <div
            v-if="projectCategory === 'all' || projectCategory === 'hardware'"
            class="glass-card flex flex-col justify-between rounded-2xl border border-slate-800 p-5 transition hover:border-cyan-500/40"
          >
            <div>
              <div class="mb-2 flex items-center justify-between gap-2">
                <h3
                  class="flex items-center gap-2 text-base font-bold text-white"
                >
                  <Train class="h-4 w-4 text-amber-400" />
                  地铁线路统一接入管控平台
                </h3>
                <span
                  class="rounded border border-amber-800 bg-amber-950/60 px-2 py-0.5 font-mono text-[10px] text-amber-300"
                  >TCP/UDP / PIS</span
                >
              </div>
              <p class="mb-4 text-xs leading-relaxed text-slate-300">
                将各子线路乘客信息系统（PIS）无缝接入中心统一服务平台，打造高可靠的地铁线路一二级协同管理体系。
              </p>
              <div
                class="mb-4 space-y-1 rounded-xl border border-slate-800/80 bg-slate-900/60 p-3 text-xs"
              >
                <div class="text-slate-400">
                  <strong class="text-slate-200">网络通信:</strong> 基于高效
                  TCP/UDP Socket 自研高吞吐通讯底层。
                </div>
                <div class="text-slate-400">
                  <strong class="text-slate-200">综合监控:</strong>
                  完美对接数据中心及通号数据接口，保障地铁调度高可靠指令收发。
                </div>
              </div>
            </div>
            <div
              class="flex flex-wrap gap-1.5 border-t border-slate-800/60 pt-2"
            >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >TCP/UDP</span
              >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >地铁PIS</span
              >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >通号系统接口</span
              >
            </div>
          </div>

          <div
            v-if="projectCategory === 'all' || projectCategory === 'hardware'"
            class="glass-card flex flex-col justify-between rounded-2xl border border-slate-800 p-5 transition hover:border-cyan-500/40"
          >
            <div>
              <div class="mb-2 flex items-center justify-between gap-2">
                <h3
                  class="flex items-center gap-2 text-base font-bold text-white"
                >
                  <Terminal class="h-4 w-4 text-rose-400" />
                  紫光及信创系统 SDK 开发
                </h3>
                <span
                  class="rounded border border-rose-800 bg-rose-950/60 px-2 py-0.5 font-mono text-[10px] text-rose-300"
                  >信创 Linux / SDK</span
                >
              </div>
              <p class="mb-4 text-xs leading-relaxed text-slate-300">
                为 OEM 厂商定制标准化驱动与
                SDK，实现在国产信创系统（中标麒麟/银河麒麟
                龙芯、兆芯版）中流畅驱动高拍仪。
              </p>
              <div
                class="mb-4 space-y-1 rounded-xl border border-slate-800/80 bg-slate-900/60 p-3 text-xs"
              >
                <div class="text-slate-400">
                  <strong class="text-slate-200">Windows 侧:</strong> 运用
                  DXShow 采集摄像头，封装成 DLL 及 ActiveX 控件。
                </div>
                <div class="text-slate-400">
                  <strong class="text-slate-200">Linux 侧:</strong> 基于 V4L2
                  架构调用摄像头，封装成原生 .so 库并提供 MFC/Qt/Web
                  端演示程序。
                </div>
              </div>
            </div>
            <div
              class="flex flex-wrap gap-1.5 border-t border-slate-800/60 pt-2"
            >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >V4L2</span
              >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >DXShow</span
              >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >ActiveX/DLL/SO</span
              >
              <span
                class="rounded bg-slate-800 px-2 py-0.5 font-mono text-[10px] text-slate-300"
                >麒麟系统</span
              >
            </div>
          </div>
        </div>
      </section>

      <div class="mb-10 grid grid-cols-1 gap-6 lg:grid-cols-3">
        <section id="skills" class="lg:col-span-2">
          <div class="mb-4 flex items-center justify-between">
            <h2 class="flex items-center gap-2 text-xl font-bold text-white">
              <Code2 class="h-5 w-5 text-cyan-400" />
              职业技能矩阵
            </h2>
          </div>

          <div
            class="glass-card space-y-4 rounded-2xl border border-slate-800 p-5"
          >
            <div>
              <div class="mb-1 flex justify-between text-xs font-mono">
                <span class="font-bold text-slate-200">C++ / Qt / MFC</span>
                <span class="text-cyan-400">熟练 (95%)</span>
              </div>
              <div class="h-2 w-full overflow-hidden rounded-full bg-slate-800">
                <div
                  class="h-full rounded-full bg-gradient-to-r from-cyan-500 to-blue-500"
                  style="width: 95%"
                ></div>
              </div>
            </div>

            <div>
              <div class="mb-1 flex justify-between text-xs font-mono">
                <span class="font-bold text-slate-200"
                  >通信协议 (TCP / UDP / MQTT / WebSocket / HTTP)</span
                >
                <span class="text-cyan-400">熟练 (90%)</span>
              </div>
              <div class="h-2 w-full overflow-hidden rounded-full bg-slate-800">
                <div
                  class="h-full rounded-full bg-gradient-to-r from-cyan-500 to-blue-500"
                  style="width: 90%"
                ></div>
              </div>
            </div>

            <div>
              <div class="mb-1 flex justify-between text-xs font-mono">
                <span class="font-bold text-slate-200"
                  >系统开发 (Windows / 信创 Linux / ARM 交叉编译)</span
                >
                <span class="text-cyan-400">熟练 (85%)</span>
              </div>
              <div class="h-2 w-full overflow-hidden rounded-full bg-slate-800">
                <div
                  class="h-full rounded-full bg-gradient-to-r from-cyan-500 to-blue-500"
                  style="width: 85%"
                ></div>
              </div>
            </div>

            <div>
              <div class="mb-1 flex justify-between text-xs font-mono">
                <span class="font-bold text-slate-200"
                  >Web GIS (Vue3 + OpenLayers + JS / HTML / CSS)</span
                >
                <span class="text-cyan-400">熟练 (80%)</span>
              </div>
              <div class="h-2 w-full overflow-hidden rounded-full bg-slate-800">
                <div
                  class="h-full rounded-full bg-gradient-to-r from-cyan-500 to-blue-500"
                  style="width: 80%"
                ></div>
              </div>
            </div>

            <div>
              <div class="mb-1 flex justify-between text-xs font-mono">
                <span class="font-bold text-slate-200"
                  >硬件SDK / 视频采集 (V4L2 / DXShow) / ActiveX / DLL</span
                >
                <span class="text-cyan-400">熟练 (85%)</span>
              </div>
              <div class="h-2 w-full overflow-hidden rounded-full bg-slate-800">
                <div
                  class="h-full rounded-full bg-gradient-to-r from-cyan-500 to-blue-500"
                  style="width: 85%"
                ></div>
              </div>
            </div>

            <div
              class="flex flex-wrap gap-2 border-t border-slate-800/80 pt-3 text-xs"
            >
              <span
                class="rounded-lg border border-slate-700 bg-slate-800/80 px-2.5 py-1 text-slate-300"
                >Visual Studio</span
              >
              <span
                class="rounded-lg border border-slate-700 bg-slate-800/80 px-2.5 py-1 text-slate-300"
                >Qt Creator</span
              >
              <span
                class="rounded-lg border border-slate-700 bg-slate-800/80 px-2.5 py-1 text-slate-300"
                >Git</span
              >
              <span
                class="rounded-lg border border-slate-700 bg-slate-800/80 px-2.5 py-1 text-slate-300"
                >串口调试助手</span
              >
              <span
                class="rounded-lg border border-slate-700 bg-slate-800/80 px-2.5 py-1 text-slate-300"
                >Wireshark抓包</span
              >
            </div>
          </div>
        </section>

        <section class="space-y-6">
          <div>
            <h2
              class="mb-4 flex items-center gap-2 text-xl font-bold text-white"
            >
              <GraduationCap class="h-5 w-5 text-cyan-400" />
              教育背景
            </h2>
            <div class="glass-card rounded-2xl border border-slate-800 p-5">
              <h3 class="text-base font-bold text-white">
                北京化工大学北方学院
              </h3>
              <p class="mt-1 font-mono text-xs text-cyan-400">
                全日制本科 | 2012.09 - 2016.07
              </p>
            </div>
          </div>

          <div>
            <h2
              class="mb-4 flex items-center gap-2 text-xl font-bold text-white"
            >
              <Award class="h-5 w-5 text-cyan-400" />
              荣誉证书
            </h2>
            <div
              class="glass-card flex flex-wrap gap-2 rounded-2xl border border-slate-800 p-5"
            >
              <span
                class="flex items-center gap-1.5 rounded-xl border border-slate-700 bg-slate-800 px-3 py-1.5 text-xs text-slate-200"
              >
                <CheckCircle class="h-3.5 w-3.5 text-emerald-400" />
                大学英语四级 (CET-4)
              </span>
              <span
                class="flex items-center gap-1.5 rounded-xl border border-slate-700 bg-slate-800 px-3 py-1.5 text-xs text-slate-200"
              >
                <CheckCircle class="h-3.5 w-3.5 text-emerald-400" />
                全国计算机二级证书
              </span>
            </div>
          </div>

          <div>
            <h2
              class="mb-4 flex items-center gap-2 text-xl font-bold text-white"
            >
              <UserCheck class="h-5 w-5 text-cyan-400" />
              自我评价
            </h2>
            <div class="glass-card rounded-2xl border border-slate-800 p-5">
              <p class="text-xs leading-relaxed text-slate-300">
                性格开朗，工作认真负责，具备强烈的责任心与灵活的逻辑思维能力。学习理解力强，不怕吃苦，具备优秀的大局观和团队协作精神，能够迅速融入团队并高效完成复杂工程攻坚任务。
              </p>
            </div>
          </div>
        </section>
      </div>

      <footer
        class="no-print mt-12 border-t border-slate-800/80 py-6 text-center text-xs font-mono text-slate-500"
      >
        <p>© 2026 胡雪源 (Hu Xueyuan) - C++ 软件工程师个人简历网页</p>
        <p class="mt-1 text-[11px] text-slate-600">
          Built with Vue 3, Tailwind CSS & Lucide Icons
        </p>
      </footer>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import {
  Award,
  Briefcase,
  CheckCircle,
  Code2,
  Copy,
  Cpu,
  GraduationCap,
  Layers,
  Mail,
  Map,
  MapPin,
  Network,
  Phone,
  Printer,
  Radar,
  Radio,
  ShieldAlert,
  SlidersHorizontal,
  Terminal,
  Train,
  UserCheck,
  Zap,
} from "@lucide/vue";

const activeTab = ref("all");
const projectCategory = ref("all");
const phoneCopied = ref(false);
const showUavDefenseImage = ref(false);
const showInterfaceImage = ref(false);
const showAutoTestImage = ref(false);
const showAoaImage = ref(false);

const copyPhone = async () => {
  try {
    await navigator.clipboard.writeText("18631456816");
  } catch (error) {
    console.warn("Clipboard access unavailable:", error);
  }

  phoneCopied.value = true;
  setTimeout(() => {
    phoneCopied.value = false;
  }, 2000);
};

const printResume = () => {
  const link = document.createElement("a");
  link.href = "/胡雪源-2026-简历.pdf";
  link.download = "胡雪源-2026-简历.pdf";
  link.target = "_blank";
  document.body.appendChild(link);
  link.click();
  document.body.removeChild(link);
};

const scrollTo = (id) => {
  const el = document.getElementById(id);
  if (el) {
    el.scrollIntoView({ behavior: "smooth" });
  }
};
</script>

<style>
body {
  background-color: #070a12;
  color: #e2e8f0;
  font-family: "Inter", sans-serif;
  background-image:
    radial-gradient(
      circle at 15% 15%,
      rgba(6, 182, 212, 0.08) 0%,
      transparent 45%
    ),
    radial-gradient(
      circle at 85% 85%,
      rgba(59, 130, 246, 0.08) 0%,
      transparent 45%
    );
  background-attachment: fixed;
}

.glass-card {
  background: rgba(17, 24, 39, 0.7);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border: 1px solid rgba(255, 255, 255, 0.08);
  box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
}

.glass-card:hover {
  border-color: rgba(56, 189, 248, 0.3);
  box-shadow: 0 10px 30px -10px rgba(6, 182, 212, 0.2);
}

::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #0a0f1d;
}

::-webkit-scrollbar-thumb {
  background: #1e293b;
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: #06b6d4;
}

@media print {
  body {
    background: #ffffff !important;
    color: #000000 !important;
  }

  .no-print {
    display: none !important;
  }

  .glass-card {
    background: #ffffff !important;
    border: 1px solid #e2e8f0 !important;
    box-shadow: none !important;
    backdrop-filter: none !important;
    color: #1a202c !important;
    break-inside: avoid;
  }

  .text-slate-300,
  .text-slate-400,
  .text-gray-300,
  .text-gray-400 {
    color: #334155 !important;
  }

  .text-cyan-400,
  .text-blue-400,
  .text-sky-400 {
    color: #0284c7 !important;
  }

  .bg-slate-800\/60,
  .bg-slate-900\/80,
  .bg-slate-800 {
    background-color: #f8fafc !important;
    border: 1px solid #e2e8f0 !important;
  }

  .print-border-b {
    border-bottom: 2px solid #0284c7 !important;
  }
}
</style>
