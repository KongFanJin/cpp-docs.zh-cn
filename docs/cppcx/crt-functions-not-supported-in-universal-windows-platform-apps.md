---
title: 通用 Windows 平台应用中不支持的 CRT 函数
description: 通用 Windows 平台应用中不支持 CRT 函数的参考指南。
ms.date: 04/16/2020
ms.assetid: cbfc957d-6c60-48f4-97e3-1ed8526743b4
ms.openlocfilehash: 793283a5c20f04e58de22fcfca5ede1926de369c
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041830"
---
# <a name="crt-functions-not-supported-in-universal-windows-platform-apps"></a>通用 Windows 平台应用中不支持的 CRT 函数

许多 C 运行时 (CRT) 函数在生成通用 Windows 平台 (UWP) 应用时不可用。 有时可以使用解决方法，例如，可以使用 Windows 运行时或 Win32 Api。 在其他情况下，CRT 函数被禁止，因为相应的功能或支持 Api 不适用于 UWP 应用。 若要查找 Windows 运行时支持的替代方法，请参阅 [UWP 应用中的 Windows api 的替代](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)方法。

下表列出了在生成 UWP 应用时不可用的 CRT 函数。 它表示任何适用的解决方法。

## <a name="unsupported-crt-functions"></a>不支持的 CRT 函数

| 函数 | 说明 | 解决方法 |
|-|-|-|
|`_beep` `_sleep` `_seterrormode`|这些函数在以前版本的 CRT 中已过时。 此外，对应 Win32 API 不可用于 UWP 应用。|无解决方法。|
|`chdir` `_chdrive` `getcwd`|这些函数已过时或不是线程安全的。|使用 `_chdir` `_getcwd` 和相关函数。|
|`_cgets` `_cgets_s` `_cgetws` `_cgetws_s` `_cprintf` `_cprintf_l` `_cprintf_p` `_cprintf_p_l` `_cprintf_s` `_cprintf_s_l` `_cputs` `_cputws` `_cscanf` `_cscanf_l` `_cscanf_s` `_cscanf_s_l` `_cwait` `_cwprintf` `_cwprintf_l` `_cwprintf_p` `_cwprintf_p_l` `_cwprintf_s` `_cwprintf_s_l` `_cwscanf` `_cwscanf_l` `_cwscanf_s` `_cwscanf_s_l` `_vcprintf` `_vcprintf_l` `_vcprintf_p` `_vcprintf_p_l` `_vcprintf_s` `_vcprintf_s_l` `_vcwprintf` `_vcwprintf_l` `_vcwprintf_p` `_vcwprintf_p_l` `_vcwprintf_s` `_vcwprintf_s_l` `_getch` `_getch_nolock` `_getche` `_getche_nolock` `_getwch` `_getwch_nolock` `_getwche` `_getwche_nolock` `_putch` `_putch_nolock` `_putwch` `_putwch_nolock` `_ungetch` `_ungetch_nolock` `_ungetwch` `_ungetwch_nolock` `_kbhit` `kbhit` `putch` `cgets` `cprintf` `cputs` `cscanf` `cwait` `getch` `getche` `ungetch`|这些函数用于直接从控制台读取和写入控制台。 UWP 应用仅限 GUI；它们不支持控制台。|无解决方法。|
|`getpid` `_getpid` | 这些函数已过时。|使用 Win32 API `GetCurrentProcessId`。|
|`_getdiskfree`|不可用。|使用 Win32 API `GetDiskFreeSpaceExW`。|
|`_getdrive` `_getdrives`|对应 API 不可用于 UWP 应用。|无解决方法。|
|`_inp` `_inpd` `_inpw` `_outp` `_outpd` `_outpw` `inp` `inpd` `inpw` `outp` `outpd` `outpw`|UWP 应用中不支持端口 IO。|无解决方法。|
|`_ismbcalnum` `_ismbcalnum_l` `_ismbcalpha` `_ismbcalpha_l` `_ismbcdigit` `_ismbcdigit_l` `_ismbcgraph` `_ismbcgraph_l` `_ismbchira` `_ismbchira_l` `_ismbckata` `_ismbckata_l` `_ismbcl0` `_ismbcl0_l` `_ismbcl1` `_ismbcl1_l` `_ismbcl2` `_ismbcl2_l` `_ismbclegal` `_ismbclegal_l` `_ismbclower` `_ismbclower_l` `_ismbcprint` `_ismbcprint_l` `_ismbcpunct` `_ismbcpunct_l` `_ismbcspace` `_ismbcspace_l` `_ismbcsymbol` `_ismbcsymbol_l` `_ismbcupper` `_ismbcupper_l` `_mbbtombc` `_mbbtombc_l` `_mbbtype` `_mbbtype_l` `_mbccpy` `_mbccpy_l` `_mbccpy_s` `_mbccpy_s_l` `_mbcjistojms` `_mbcjistojms_l` `_mbcjmstojis` `_mbcjmstojis_l` `_mbclen` `_mbclen_l` `_mbctohira` `_mbctohira_l` `_mbctokata` `_mbctokata_l` `_mbctolower` `_mbctolower_l` `_mbctombb` `_mbctombb_l` `_mbctoupper` `_mbctoupper_l` `_mbsbtype` `_mbsbtype_l` `_mbscat` `_mbscat_l` `_mbscat_s` `_mbscat_s_l` `_mbschr` `_mbschr_l` `_mbscmp` `_mbscmp_l` `_mbscoll` `_mbscoll_l` `_mbscpy` `_mbscpy_l` `_mbscpy_s` `_mbscpy_s_l` `_mbscspn` `_mbscspn_l` `_mbsdec` `_mbsdec_l` `_mbsicmp` `_mbsicmp_l` `_mbsicoll` `_mbsicoll_l` `_mbsinc` `_mbsinc_l` `_mbslen` `_mbslen_l` `_mbslwr` `_mbslwr_l` `_mbslwr_s` `_mbslwr_s_l` `_mbsnbcat` `_mbsnbcat_l` `_mbsnbcat_s` `_mbsnbcat_s_l` `_mbsnbcmp` `_mbsnbcmp_l` `_mbsnbcnt` `_mbsnbcnt_l` `_mbsnbcoll` `_mbsnbcoll_l` `_mbsnbcpy` `_mbsnbcpy_l` `_mbsnbcpy_s` `_mbsnbcpy_s_l` `_mbsnbicmp` `_mbsnbicmp_l` `_mbsnbicoll` `_mbsnbicoll_l` `_mbsnbset` `_mbsnbset_l` `_mbsnbset_s` `_mbsnbset_s_l` `_mbsncat` `_mbsncat_l` `_mbsncat_s` `_mbsncat_s_l` `_mbsnccnt` `_mbsnccnt_l` `_mbsncmp` `_mbsncmp_l` `_mbsncoll` `_mbsncoll_l` `_mbsncpy` `_mbsncpy_l` `_mbsncpy_s` `_mbsncpy_s_l` `_mbsnextc` `_mbsnextc_l` `_mbsnicmp` `_mbsnicmp_l` `_mbsnicoll` `_mbsnicoll_l` `_mbsninc` `_mbsninc_l` `_mbsnlen` `_mbsnlen_l` `_mbsnset` `_mbsnset_l` `_mbsnset_s` `_mbsnset_s_l` `_mbspbrk` `_mbspbrk_l` `_mbsrchr` `_mbsrchr_l` `_mbsrev` `_mbsrev_l` `_mbsset` `_mbsset_l` `_mbsset_s` `_mbsset_s_l` `_mbsspn` `_mbsspn_l` `_mbsspnp` `_mbsspnp_l` `_mbsstr` `_mbsstr_l` `_mbstok` `_mbstok_l` `_mbstok_s` `_mbstok_s_l` `_mbsupr` `_mbsupr_l` `_mbsupr_s` `_mbsupr_s_l` `is_wctype`|UWP 应用中不支持多字节字符串。|改为使用 Unicode 字符串。|
|`_pclose` `_pipe` `_popen` `_wpopen`|管道功能不可用于 UWP 应用。|无解决方法。|
|`_resetstkoflw`|支持 Win32 API 不可用于 UWP 应用。|无解决方法。|
|`_getsystime` `_setsystime`|这些是以前 CRT 版本中的已过时 API。 此外，用户无法在 UWP 应用中设置系统时间，因为缺少权限。|若要只获取系统时间，请使用 Win32 API `GetSystemTime`。 无法设置系统时间。|
|`_environ``_putenv` `_putenv_s` `_searchenv``_searchenv_s` `_dupenv_s` `_wputenv``_wputenv_s` `_wsearchenv` getenv `_wdupenv_s` `_wenviron` getenv_s `_wgetenv` putenv `_wgetenv_s` `_wsearchenv_s``tzset`|环境变量不可用于 UWP 应用。|无解决方法。 若要设置时区，请使用 `_tzset` 。|
|`_loaddll` `_getdllprocaddr` `_unloaddll`|这些是以前 CRT 版本中的已过时函数。 此外，用户也不能加载同一个应用程序包中的 Dll。|使用 Win32 API `LoadPackagedLibrary`、 `GetProcAddress`和 `FreeLibrary` 加载和使用打包的 DLL。|
|`_wexecl` `_wexecle` `_wexeclp` `_wexeclpe` `_wexecv` `_wexecve` `_wexecvp` `_wexecvpe` `_execl` `_execle` `_execlp` `_execlpe` `_execv` `_execve` `_execvp` `_execvpe` `_spawnl` `_spawnle` `_spawnlp` `_spawnlpe` `_spawnv` `_spawnve` `_spawnvp` `_spawnvpe` `_wspawnl` `_wspawnle` `_wspawnlp` `_wspawnlpe` `_wspawnv` `_wspawnve` `_wspawnvp` `_wspawnvpe` `_wsystem` `execl` `execle` `execlp` `execlpe` `execv` `execve` `execvp` `execvpe` `spawnl` `spawnle` `spawnlp` `spawnlpe` `spawnv` `spawnve` `spawnvp` `spawnvpe` `system`|该功能在 UWP 应用中不可用。 UWP 应用无法调用另一个 UWP 应用或桌面应用。|无解决方法。|
|`_heapwalk` `_heapadd` `_heapchk` `_heapset` `_heapused`|这些函数通常用于处理堆。 但是，UWP 应用中不支持对应 Win32 API。 而且，应用无法再创建或使用专用堆。|无解决方法。 但是， `_heapwalk` 在 DEBUG CRT 中可用（仅用于进行调试）。 无法在上载到 Microsoft Store 的应用中使用这些功能。|

对于 UWP 应用，以下函数在 CRT 中可用。 但是，仅当你无法使用相应的 Win32 或 Windows 运行时 Api 时（例如，当你移植大型代码库时）才使用它们：

| 函数 | 解决方法 |
|-|-|
|单字节字符串函数（例如， `strcat`、 `strcpy`、 `strlwr`等）。|使 UWP 应用严格成为 Unicode，因为公开的所有 Win32 Api 和 Windows 运行时 Api 都仅使用 Unicode 字符集。  对于移植大型代码库，可以保留单字节函数，但应避免这样做。 应尽可能使用相应的宽字符函数。|
|流 IO 和低级文件 IO 函数（例如， `fopen`、 `open`等）。|这些函数是同步的，不推荐用于 UWP 应用。 在 UWP 应用中，使用异步 API 打开、读取和写入文件，以防止锁定 UI 线程。 这类 API 的示例是在 `Windows::Storage::FileIO` 类中的一个。|

## <a name="windows-8x-store-apps-and-windows-phone-8x-apps"></a>Windows 8.x 应用商店应用和 Windows Phone 8.x 应用

前面提到的 Api 和以下 Api 在 Windows 8.x 应用商店应用和 Windows Phone 8.x 应用中不可用。

| 函数 | 说明 | 解决方法 |
|-|-|-|
|`_beginthread` `_beginthreadex` `_endthread` `_endthreadex`|线程处理 Win32 API 在 Windows 8.x 应用商店应用中不可用。|改用 `Windows Runtime Windows::System::Threading::ThreadPool` 或 `concurrency::task` 。|
|`_chdir` `_wchdir` `_getcwd` `_getdcwd` `_wgetcwd` `_wgetdcwd`|工作目录的概念不适用于 Windows 8.x 应用商店应用。|改用完整路径。|
|`_isleadbyte_l` `_ismbbalnum`, `_ismbbalnum_l`, `_ismbbalpha`, `_ismbbalpha` `_ismbbalpha_l` `_ismbbgraph` `_ismbbgraph_l` `_ismbbkalnum` `_ismbbkalnum_l` `_ismbbkana` `_ismbbkana_l` `_ismbbkprint` `_ismbbkprint_l` `_ismbbkpunct` `_ismbbkpunct_l` `_ismbblead` `_ismbblead_l` `_ismbbprint` `_ismbbprint_l` `_ismbbpunct` `_ismbbpunct_l` `_ismbbtrail` `_ismbbtrail_l` `_ismbslead` `_ismbslead_l` `_ismbstrail` `_ismbstrail_l` `_mbsdup` `isleadbyte`|Windows 8.x 应用商店应用中不支持多字节字符串。|改为使用 Unicode 字符串。|
|`_tzset`|环境变量不可用于 Windows 8.x 应用商店应用。|无解决方法。|
|`_get_heap_handle`, `_heapmin`|Windows 8.x 应用商店应用中不支持对应 Win32 API。 而且，应用无法再创建专用堆。|无解决方法。 但是， ``_get_heap_handle`` 在 DEBUG CRT 中可用（仅用于进行调试）。|
