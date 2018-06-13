---
title: Wdrażanie aplikacji, które odwołują się do formantów Powerpack (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
ms.openlocfilehash: bd235bc0b4a7f9978333931ae1dce012c0950374
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587508"
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a>Wdrażanie aplikacji, które odwołują się do formantów Powerpack (Visual Studio)
Jeśli chcesz wdrożyć aplikację, która odwołuje się do formantów Powerpack (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, lub <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), kontrolki musi być zainstalowany na komputerze docelowym.  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a>Instalowanie formantów Powerpack jako warunek wstępny  
 Aby pomyślnie wdrożyć aplikację, należy wdrożyć wszystkie składniki, które są używane przez aplikację. Proces instalowania składników wymaganych wstępnie nosi nazwę *uruchamianie*.  
  
 Po zainstalowaniu programu Visual Studio na komputerze deweloperskim, pakiet programu inicjującego Powerpack jest dodawany do katalogu zawierającego program inicjujący Instalatora programu Visual Studio. Ten pakiet jest dostępna po wykonaniu procedury dodawania wymagania wstępne dotyczące albo [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] lub wdrożenia Instalatora Windows.  
  
 Domyślnie zainicjowano składniki są wdrażane z tej samej lokalizacji co pakiet instalacyjny. Alternatywnie można wdrożyć składniki z adresu URL lub pliku lokalizację udziału, w którym użytkownicy mogą pobrać je w razie potrzeby.  
  
> [!NOTE]
>  Aby zainstalować składniki zainicjowano, użytkownik może być konieczne uprawnienia użytkownika administracyjnego lub podobne na komputerze. Dla [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplikacji, oznacza to, że użytkownik będzie musiał uprawnień administracyjnych do zainstalowania aplikacji, niezależnie od poziomu zabezpieczeń, określonym przez aplikację. Po zainstalowaniu aplikacji, użytkownik będzie mógł uruchomić aplikację bez uprawnień administracyjnych.  
  
 Podczas instalacji użytkownicy otrzymują monit do zainstalowania formantów Powerpack, jeśli nie są dostępne na komputerze docelowym.  
  
 Alternatywą wobec uruchamianie wstępnie wdrożeniem formantów Powerpack przy użyciu systemu dystrybucji oprogramowania elektronicznych, takich jak Microsoft Systems Management Server.  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [Formantów Powerpack Visual Basic](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
