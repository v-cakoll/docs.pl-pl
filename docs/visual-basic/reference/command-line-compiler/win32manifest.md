---
title: -win32manifest
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: cef1e6c19e7fdd6fc9f42c8fc36008314ea80a80
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349132"
---
# <a name="-win32manifest-visual-basic"></a>-WIN32MANIFEST (Visual Basic)
Identyfikuje zdefiniowany przez użytkownika plik manifestu aplikacji Win32, który ma zostać osadzony w przenośnym pliku wykonywalnym (PE) projektu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`fileName`|Ścieżka pliku manifestu niestandardowego.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie kompilator Visual Basic osadza manifest aplikacji, który określa żądany poziom wykonywania jako źródło. Tworzy manifest w tym samym folderze, w którym plik wykonywalny jest kompilowany, zazwyczaj folder bin\Debug lub bin\Release w przypadku korzystania z programu Visual Studio. Jeśli chcesz podać niestandardowy manifest, na przykład aby określić żądany poziom wykonywania najwyższe dostępne lub wymaga administratora, Użyj tej opcji, aby określić nazwę pliku.  
  
> [!NOTE]
> Ta opcja i opcja [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) wykluczają się wzajemnie. Jeśli spróbujesz użyć obu opcji w tym samym wierszu polecenia, zostanie wyświetlony błąd kompilacji.  
  
 Aplikacja, która nie ma manifestu aplikacji, która określa żądany poziom wykonania, będzie podlegała wirtualizacji plików/rejestru w ramach funkcji kontroli konta użytkownika w systemie Windows Vista. Aby uzyskać więcej informacji na temat wirtualizacji, zobacz [wdrażanie ClickOnce w systemie Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).  
  
 Aplikacja będzie podlegać wirtualizacji, jeśli spełniony jest jeden z następujących warunków:  
  
1. Używasz opcji `-nowin32manifest` i nie udostępniasz manifestu w późniejszym kroku kompilacji lub jako część pliku zasobów systemu Windows (. res) przy użyciu opcji `-win32resource`.  
  
2. Należy podać niestandardowy manifest, który nie określa żądanego poziomu wykonania.  
  
 Program Visual Studio tworzy domyślny plik. manifest i zapisuje go w katalogach debugowania i wydań obok pliku wykonywalnego. Możesz wyświetlić lub edytować domyślny plik aplikacji. manifest, klikając pozycję **Wyświetl ustawienia kontroli konta użytkownika** na karcie **aplikacja** w projektancie projektu. Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 Można dostarczyć manifest aplikacji jako niestandardowy krok po kompilacji lub jako część pliku zasobów Win32 przy użyciu opcji `-nowin32manifest`. Użyj tej samej opcji, jeśli chcesz, aby aplikacja podlegała wirtualizacji plików lub rejestru w systemie Windows Vista. Uniemożliwi to kompilatorowi utworzenie i osadzenie domyślnego manifestu w pliku PE.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje domyślny manifest, który kompilator Visual Basic wstawia do PE.  
  
> [!NOTE]
> Kompilator wstawia standardową nazwę aplikacji aplikacja. app do manifestu XML. Jest to obejście, aby umożliwić uruchamianie aplikacji w systemie Windows Server 2003 z dodatkiem Service Pack 3.  
  
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

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
