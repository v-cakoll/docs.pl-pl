---
title: -win32manifest (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 36a16f1ee037a1379399c7ee2e2c67427eb9d1b2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-win32manifest-c-compiler-options"></a>-win32manifest (opcje kompilatora C#)
Użyj **-win32manifest** opcję, aby określić użytkownika aplikacji plik manifestu Win32 do osadzenia pliku przenośny plik wykonywalny (PE) projektu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Nazwę i lokalizację niestandardowego pliku manifestu.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie [!INCLUDE[csharp_current_short](~/includes/csharp-current-short-md.md)] kompilatora osadza manifest aplikacji, która określa wymagany poziom wykonywania elementu "asInvoker". W tym samym folderze, w którym plik wykonywalny jest wbudowana, zwykle folderu bin\Debug lub bin\Release, gdy używasz programu Visual Studio tworzy plik manifestu. Jeśli chcesz podać niestandardowy manifest, na przykład określić wymagany poziom wykonywania "highestAvailable" lub "requireAdministrator", ta opcja umożliwia Określ nazwę pliku.  
  
> [!NOTE]
>  Ta opcja i [-win32res (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) opcji wzajemnie się wykluczają. Jeśli spróbujesz użyć obu opcji, w tym samym wierszu polecenia wystąpi błąd kompilacji.  
  
 Aplikacja, która nie ma aplikacji manifestu, który określa wymagany poziom wykonywania podlegają wirtualizacji plików/rejestru w funkcji Kontrola konta użytkownika w systemie Windows. Aby uzyskać więcej informacji, zobacz [Kontrola konta użytkownika](/windows/access-protection/user-account-control/user-account-control-overview).  
  
 Aplikacji będą podlegać wirtualizacji, jeśli jest spełniony jeden z następujących warunków:  
  
-   Możesz użyć **-nowin32manifest** opcja i nie udostępniają manifestu w kolejnym kroku kompilacji lub jako część pliku zasobów systemu Windows (.res) przy użyciu **-win32res** opcji.  
  
-   Musisz podać niestandardowy manifest, która nie określa wymagany poziom wykonywania.  
  
 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]tworzy domyślny plik .manifest i zapisuje go w katalogach debug i release obok pliku wykonywalnego. Aby dodać niestandardowy manifest, tworząc go w edytorze tekstu, a następnie dodanie go do projektu. Alternatywnie możesz kliknąć prawym przyciskiem myszy **projektu** ikonę w **Eksploratora rozwiązań**, kliknij przycisk **Dodaj nowy element**, a następnie kliknij przycisk **plikumanifestuaplikacji**. Po dodaniu nowego lub istniejącego pliku manifestu, zostanie wyświetlony na **manifestu** listy rozwijanej. Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Możesz podać manifest aplikacji jako niestandardowy krok kompilacji po lub w ramach plik zasobów Win32 za pomocą [-nowin32manifest (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) opcji. Tej samej opcji należy użyć, jeśli aplikacja ma być może ulec plików lub rejestrze wirtualizacji w systemie Windows Vista. Uniemożliwi to kompilatora tworzenie i osadzanie manifestu domyślne w przenośny plik wykonywalny (PE).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono manifest domyślny, że kompilator Visual C# wstawia do PE.  
  
> [!NOTE]
>  Kompilator Wstawia nazwę standardowej aplikacji "MyApplication.app" do pliku xml. To obejście, aby umożliwić aplikacji do uruchamiania w systemie Windows Server 2003 Service Pack 3.  
  
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
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [-nowin32manifest (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
