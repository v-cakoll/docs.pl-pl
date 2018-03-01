---
title: "Wdrażanie aplikacji, które odwołują się do wyniku składnik PrintForm (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 15b6e21e769c90e23e66e4f87b37f74462423985
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a>Wdrażanie aplikacji, które odwołują się do wyniku składnik PrintForm (Visual Basic)
Jeśli chcesz wdrożyć aplikację, która odwołuje się do <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika, składnik musi być zainstalowany na komputerze docelowym.  
  
 Formantów PowerPack nie są uwzględnione w programie Visual Studio, ale można pobrać je z [Centrum pobierania](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="installing-the-printform-as-a-prerequisite"></a>Instalowanie PrintForm jako warunek wstępny  
 Aby pomyślnie wdrożyć aplikację, należy wdrożyć wszystkie składniki, które są używane przez aplikację. Proces instalowania składników wymaganych wstępnie nosi nazwę *uruchamianie*.  
  
 Gdy <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnik jest zainstalowany na komputerze deweloperskim, pakiet programu inicjującego Microsoft Visual Basic Powerpack jest dodawany do [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] katalogu programu inicjującego. Ten pakiet jest dostępna po wykonaniu procedury dodawania wymagania wstępne dotyczące albo [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] lub wdrożenia Instalatora Windows.  
  
 Domyślnie zainicjowano składniki są wdrażane z tej samej lokalizacji co pakiet instalacyjny. Alternatywnie można wdrożyć składniki z adresu URL lub pliku lokalizację udziału, w którym użytkownicy mogą pobrać je w razie potrzeby.  
  
> [!NOTE]
>  Aby zainstalować składniki zainicjowano, użytkownik może być konieczne uprawnienia użytkownika administracyjnego lub podobne na komputerze. Dla [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplikacji, oznacza to, że użytkownik będzie musiał uprawnień administracyjnych do zainstalowania aplikacji, niezależnie od poziomu zabezpieczeń, określonym przez aplikację. Po zainstalowaniu aplikacji, użytkownik będzie mógł uruchomić aplikację bez uprawnień administracyjnych.  
  
 Podczas instalacji, użytkownicy będą monitowani do zainstalowania <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składników, jeśli nie ma go na komputerze docelowym.  
  
 Alternatywą dla uruchamianie przed wdrożeniem <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika przy użyciu systemu dystrybucji oprogramowania elektronicznych, takich jak Microsoft Systems Management Server.  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: Instalowanie wymagań wstępnych za pomocą aplikacji ClickOnce](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [Składnik PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)
