---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 901ea984a8e8e90329953a8936e68f2fc07f8847
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="-win32manifest-visual-basic"></a>-win32manifest (Visual Basic)
Identyfikuje użytkownika aplikacji plik manifestu Win32 do osadzenia pliku przenośny plik wykonywalny (PE) projektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`fileName`|Ścieżka niestandardowego pliku manifestu.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie kompilator Visual Basic osadza manifest aplikacji, która określa poziom wykonywania żądany asInvoker. W tym samym folderze, w którym plik wykonywalny jest wbudowana, zwykle folderu bin\Debug lub bin\Release, gdy używasz programu Visual Studio tworzy plik manifestu. Jeśli chcesz podać niestandardowy manifest, na przykład określić wymagany poziom wykonywania highestAvailable lub requireAdministrator, ta opcja umożliwia Określ nazwę pliku.  
  
> [!NOTE]
>  Ta opcja i [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) opcji wzajemnie się wykluczają. Jeśli spróbujesz użyć obu opcji, w tym samym wierszu polecenia, wystąpi błąd kompilacji.  
  
 Aplikacja, która nie ma aplikacji manifestu, który określa wymagany poziom wykonywania podlegają wirtualizacji plików/rejestru w funkcji Kontrola konta użytkownika w systemie Windows Vista. Aby uzyskać więcej informacji o wirtualizacji, zobacz [wdrażania ClickOnce w systemie Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).  
  
 Aplikacji będą podlegać wirtualizacji, jeśli jest spełniony jeden z następujących warunków:  
  
1.  Możesz użyć `-nowin32manifest` opcja i nie udostępniają manifestu w kolejnym kroku kompilacji lub jako część pliku zasobów systemu Windows (.res) przy użyciu `-win32resource` opcji.  
  
2.  Musisz podać niestandardowy manifest, która nie określa wymagany poziom wykonywania.  
  
 Visual Studio tworzy domyślny plik .manifest i zapisuje go w katalogach debug i release obok pliku wykonywalnego. Umożliwia wyświetlenie i edytowanie pliku app.manifest domyślny, klikając **ustawienia kontroli konta użytkownika widoku** na **aplikacji** kartę w Projektancie projektu. Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 Możesz podać manifest aplikacji jako niestandardowy krok kompilacji po lub w ramach plik zasobów Win32 przy użyciu `-nowin32manifest` opcji. Tej samej opcji należy użyć, jeśli aplikacja ma być może ulec plików lub rejestrze wirtualizacji w systemie Windows Vista. Uniemożliwi to kompilatora tworzenie i osadzanie manifestu domyślnej w pliku PE.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono manifest domyślny, że kompilator Visual Basic wstawia do PE.  
  
> [!NOTE]
>  Nazwa standardowa aplikacji MyApplication.app zostanie wstawiona do manifestu XML. To obejście, aby umożliwić aplikacji do uruchamiania w systemie Windows Server 2003 Service Pack 3.  
  
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
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
