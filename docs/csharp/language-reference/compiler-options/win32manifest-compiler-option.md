---
title: -win32manifest (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
ms.openlocfilehash: 24677b145974af03e6ddcac1b9bab5907ab70c7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69924675"
---
# <a name="-win32manifest-c-compiler-options"></a>-win32manifest (Opcje kompilatora C#)
Użyj opcji **-win32manifest,** aby określić zdefiniowany przez użytkownika plik manifestu aplikacji Win32, który ma być osadzony w przenośnym pliku wykonywalnym projektu (PE).  
  
## <a name="syntax"></a>Składnia  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Nazwa i lokalizacja pliku manifestu niestandardowego.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie kompilator języka Visual C# osadza manifest aplikacji, który określa żądany poziom wykonania "asInvoker". Tworzy manifest w tym samym folderze, w którym jest zbudowany plik wykonywalny, zazwyczaj bin\Debug lub bin\Release folderu podczas korzystania z programu Visual Studio. Jeśli chcesz podać manifest niestandardowy, na przykład, aby określić żądany poziom wykonania "highestAvailable" lub "requireAdministrator", użyj tej opcji, aby określić nazwę pliku.  
  
> [!NOTE]
> Ta opcja i [-win32res (Opcje kompilatora C#)](./win32res-compiler-option.md) są wzajemnie się wykluczają. Jeśli spróbujesz użyć obu opcji w tym samym wierszu polecenia pojawi się błąd kompilacji.  
  
 Aplikacja, która nie ma manifestu aplikacji, który określa żądany poziom wykonania będzie podlegać wirtualizacji pliku/rejestru w ramach funkcji Kontrola konta użytkownika w systemie Windows. Aby uzyskać więcej informacji, zobacz [Kontrola konta użytkownika](/windows/access-protection/user-account-control/user-account-control-overview).  
  
 Aplikacja będzie podlegać wirtualizacji, jeśli którykolwiek z tych warunków jest spełniony:  
  
- Użyj opcji **-nowin32manifest** i nie udostępniasz manifestu w późniejszym kroku kompilacji lub jako część pliku Windows Resource (.res) przy użyciu opcji **-win32res.**  
  
- Należy podać manifest niestandardowy, który nie określa żądanego poziomu wykonania.  
  
 Visual Studio tworzy domyślny plik manifestu i przechowuje go w katalogach debugowania i wydania obok pliku wykonywalnego. Manifest niestandardowy można dodać, tworząc go w dowolnym edytorze tekstu, a następnie dodając plik do projektu. Alternatywnie można kliknąć prawym przyciskiem myszy ikonę **projektu** w **Eksploratorze rozwiązań,** kliknąć polecenie **Dodaj nowy element**, a następnie kliknąć polecenie Plik **manifestu aplikacji**. Po dodaniu nowego lub istniejącego pliku manifestu pojawi się on na liście rozwijanej **Manifest.** Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Manifest aplikacji można podać jako niestandardowy krok po kompilacji lub jako część pliku zasobów Win32 przy użyciu opcji [-nowin32manifest (C# Compiler Options).](./nowin32manifest-compiler-option.md) Użyj tej samej opcji, jeśli chcesz, aby aplikacja podlegała wirtualizacji plików lub rejestru w systemie Windows Vista. Uniemożliwi to kompilatorowi tworzenie i osadzanie domyślnego manifestu w przenośnym pliku wykonywalnym (PE).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono domyślny manifest, który kompilator Visual C# wstawia do programu PE.  
  
> [!NOTE]
> Kompilator wstawia standardową nazwę aplikacji " MyApplication.app " do pliku xml. Jest to obejście umożliwiające uruchamianie aplikacji w systemie Windows Server 2003 z dodatkiem Service Pack 3.  
  
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

- [Opcje kompilatora Języka C#](./index.md)
- [-nowin32manifest (Opcje kompilatora C#)](./nowin32manifest-compiler-option.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
