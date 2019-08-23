---
title: -WIN32MANIFEST (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
ms.openlocfilehash: 24677b145974af03e6ddcac1b9bab5907ab70c7b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924675"
---
# <a name="-win32manifest-c-compiler-options"></a>-WIN32MANIFEST (C# opcje kompilatora)
Użyj opcji **-WIN32MANIFEST** , aby określić zdefiniowany przez użytkownika plik manifestu aplikacji Win32, który ma zostać osadzony w przenośnym pliku wykonywalnym (PE) projektu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Nazwa i lokalizacja pliku manifestu niestandardowego.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie kompilator wizualny C# osadzi manifest aplikacji, który określa żądany poziom wykonywania "jako Źródło". Tworzy manifest w tym samym folderze, w którym jest skompilowany plik wykonywalny, zazwyczaj folder bin\Debug lub bin\Release w przypadku korzystania z programu Visual Studio. Jeśli chcesz podać niestandardowy manifest, na przykład aby określić żądany poziom wykonywania "najwyższe dostępne" lub "wymaga administratora", Użyj tej opcji, aby określić nazwę pliku.  
  
> [!NOTE]
> Ta opcja i opcja [-win32res — (C# opcje kompilatora)](./win32res-compiler-option.md) wzajemnie się wykluczają. Jeśli spróbujesz użyć obu opcji w tym samym wierszu polecenia, zostanie wyświetlony błąd kompilacji.  
  
 Aplikacja, która nie ma manifestu aplikacji, która określa żądany poziom wykonania, będzie podlegała wirtualizacji plików/rejestru w ramach funkcji kontroli konta użytkownika w systemie Windows. Aby uzyskać więcej informacji, zobacz [Kontrola konta użytkownika](/windows/access-protection/user-account-control/user-account-control-overview).  
  
 Aplikacja będzie podlegać wirtualizacji, jeśli spełniony jest jeden z następujących warunków:  
  
- Użyj opcji **-nowin32manifest** i nie udostępniasz manifestu w późniejszym kroku kompilacji lub jako część pliku zasobów systemu Windows (. res) przy użyciu opcji **-win32res —** .  
  
- Należy podać niestandardowy manifest, który nie określa żądanego poziomu wykonania.  
  
 Program Visual Studio tworzy domyślny plik. manifest i zapisuje go w katalogach debugowania i wydań obok pliku wykonywalnego. Można dodać manifest niestandardowy, tworząc jeden w dowolnym edytorze tekstu, a następnie dodając plik do projektu. Alternatywnie możesz kliknąć prawym przyciskiem myszy ikonę **projektu** w **Eksplorator rozwiązań**, kliknąć pozycję **Dodaj nowy element**, a następnie kliknąć pozycję **plik manifestu aplikacji**. Po dodaniu nowego lub istniejącego pliku manifestu zostanie on wyświetlony na liście rozwijanej **manifestu** . Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektuC#()](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Można dostarczyć manifest aplikacji jako niestandardowy krok po kompilacji lub jako część pliku zasobów Win32 przy użyciu opcji [-nowin32manifest (C# opcje kompilatora)](./nowin32manifest-compiler-option.md) . Użyj tej samej opcji, jeśli chcesz, aby aplikacja podlegała wirtualizacji plików lub rejestru w systemie Windows Vista. Uniemożliwi to kompilatorowi utworzenie i osadzenie domyślnego manifestu w przenośnym pliku wykonywalnym (PE).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano domyślny manifest wstawiany przez kompilator wizualny C# do środowiska PE.  
  
> [!NOTE]
> Kompilator wstawia w kodzie XML standardową nazwę aplikacji "moja aplikacja. aplikacja". Jest to obejście, aby umożliwić uruchamianie aplikacji w systemie Windows Server 2003 z dodatkiem Service Pack 3.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [-nowin32manifest (C# opcje kompilatora)](./nowin32manifest-compiler-option.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
