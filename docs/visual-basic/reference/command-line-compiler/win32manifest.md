---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: 15fe62457ed11ffcd08a1db3aa8be57080f22869
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300801"
---
# <a name="-win32manifest-visual-basic"></a>-win32manifest (Visual Basic)
Identyfikuje użytkownika aplikacji plik manifestu Win32 osadzanego do projektu przenośnych plików wykonywalnych (PE) pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`fileName`|Ścieżka niestandardowego pliku manifestu.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie kompilator języka Visual Basic osadza manifest aplikacji, która określa wymagany poziom wykonywania programu asInvoker. Tworzy manifest w tym samym folderze, w którym plik wykonywalny został opracowany, zwykle bin\Debug lub bin\Release folderu, gdy używasz programu Visual Studio. Jeśli chcesz podać niestandardowy manifest, na przykład aby określić wymagany poziom wykonywania highestAvailable lub requireAdministrator, należy użyć tę opcję, aby określić nazwę pliku.  
  
> [!NOTE]
>  Ta opcja i [-win32resource —](../../../visual-basic/reference/command-line-compiler/win32resource.md) opcji wzajemnie się wykluczają. Jeśli spróbujesz użyć obu opcji w tym samym wierszu polecenia, zostanie wyświetlony błąd kompilacji.  
  
 Aplikacja, która ma żadna aplikacja manifestu, który określa, że będzie wymagany poziom wykonywania pliku/rejestru wirtualizacji w ramach funkcji kontroli konta użytkownika w Windows Vista. Aby uzyskać więcej informacji na temat wirtualizacji, zobacz [wdrażania ClickOnce w systemie Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).  
  
 Twoja aplikacja będzie wirtualizacji, jeśli jest spełniony jeden z następujących warunków:  
  
1. Możesz użyć `-nowin32manifest` opcji nie są oferowane manifest na późniejszym etapie kompilacji lub jako część pliku Windows zasobów (.res) przy użyciu `-win32resource` opcji.  
  
2. Możesz podać niestandardowy manifest, który nie określa wymagany poziom wykonywania.  
  
 Visual Studio tworzy domyślny plik .manifest i zapisuje go w katalogach debug i release, wraz z pliku wykonywalnego. Możesz wyświetlić lub edytować plik app.manifest domyślny, klikając **ustawienia funkcji Kontrola konta użytkownika widoku** na **aplikacji** kartę w Projektancie projektu. Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 Możesz podać w manifeście aplikacji jako niestandardowy krok po kompilacji lub jako część pliku zasobów Win32 przy użyciu `-nowin32manifest` opcji. Jeśli chcesz, aby aplikacja ma być wirtualizacji plików i rejestru w systemie Windows Vista, należy użyć tej samej opcji. Uniemożliwi to kompilatora od utworzenia i osadzanie manifestu domyślnej w pliku PE.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia domyślny manifest, kompilator Visual Basic wstawia do PE.  
  
> [!NOTE]
>  Kompilator Wstawia nazwę standardowej aplikacji MyApplication.app do manifestu XML. To obejście, aby umożliwić aplikacji do uruchamiania w systemie Windows Server 2003 z dodatkiem Service Pack 3.  
  
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

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
