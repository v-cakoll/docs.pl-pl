---
title: -win32manifest (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
ms.openlocfilehash: 88932ad30e30d53312e6d76f70415969b9e86675
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517983"
---
# <a name="-win32manifest-c-compiler-options"></a>-win32manifest (opcje kompilatora C#)
Użyj **-win32manifest** opcję, aby określić zdefiniowanych przez użytkownika aplikacji plik manifestu Win32 osadzanego do projektu przenośnych plików wykonywalnych (PE) pliku.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Nazwę i lokalizację niestandardowego pliku manifestu.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie kompilator Visual C# osadza manifest aplikacji, która określa wymagany poziom wykonywania programu "asInvoker". Tworzy manifest w tym samym folderze, w którym plik wykonywalny został opracowany, zwykle bin\Debug lub bin\Release folderu, gdy używasz programu Visual Studio. Jeśli chcesz podać niestandardowy manifest, na przykład aby określić wymagany poziom wykonywania "highestAvailable" lub "requireAdministrator", należy użyć tę opcję, aby określić nazwę pliku.  
  
> [!NOTE]
>  Ta opcja i [-win32res (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) opcji wzajemnie się wykluczają. Jeśli spróbujesz użyć obu opcji w tym samym wierszu polecenia zostanie wyświetlony błąd kompilacji.  
  
 Aplikacja, która ma żadna aplikacja manifestu, który określa, że będzie wymagany poziom wykonywania pliku/rejestru wirtualizacji w ramach tej funkcji Kontrola konta użytkownika w programie Windows. Aby uzyskać więcej informacji, zobacz [Kontrola konta użytkownika](/windows/access-protection/user-account-control/user-account-control-overview).  
  
 Twoja aplikacja będzie wirtualizacji, jeśli jest spełniony jeden z następujących warunków:  
  
-   Możesz użyć **-nowin32manifest** opcji nie są oferowane manifest na późniejszym etapie kompilacji lub jako część pliku Windows zasobów (.res) przy użyciu **-win32res** opcji.  
  
-   Możesz podać niestandardowy manifest, który nie określa wymagany poziom wykonywania.  
  
 Visual Studio tworzy domyślny plik .manifest i zapisuje go w katalogach debug i release, wraz z pliku wykonywalnego. Aby dodać niestandardowy manifest, tworząc go w dowolnym edytorze tekstów, a następnie dodanie go do projektu. Alternatywnie możesz kliknąć prawym przyciskiem myszy **projektu** ikonę **Eksploratora rozwiązań**, kliknij przycisk **Dodaj nowy element**, a następnie kliknij przycisk **Plikmanifestuaplikacji**. Po dodaniu nowego lub istniejącego pliku manifestu, pojawi się na **manifestu** listy rozwijanej. Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Możesz podać w manifeście aplikacji jako niestandardowy krok po kompilacji lub jako część pliku zasobów Win32 przy użyciu [-nowin32manifest (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) opcji. Jeśli chcesz, aby aplikacja ma być wirtualizacji plików i rejestru w systemie Windows Vista, należy użyć tej samej opcji. Uniemożliwi to kompilatora od utworzenia i osadzanie domyślny manifest w przenośny plik wykonywalny (PE).  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia domyślny manifest, kompilator Visual C#, wstawia w Wykonywalnym.  
  
> [!NOTE]
>  Kompilator Wstawia nazwę standardowej aplikacji "MyApplication.app" do pliku xml. To obejście, aby umożliwić aplikacji do uruchamiania w systemie Windows Server 2003 z dodatkiem Service Pack 3.  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a>Zobacz też  

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [-nowin32manifest (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
