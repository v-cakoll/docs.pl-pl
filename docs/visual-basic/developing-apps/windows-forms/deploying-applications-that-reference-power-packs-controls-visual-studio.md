---
title: Wdrażanie aplikacji, które odwołują się do formantów Powerpack (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
ms.openlocfilehash: bd235bc0b4a7f9978333931ae1dce012c0950374
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39198231"
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a>Wdrażanie aplikacji, które odwołują się do formantów Powerpack (Visual Studio)
Jeśli chcesz wdrożyć aplikację, która odwołuje się do formantów Powerpack (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, lub <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), kontrolek, musi być zainstalowany na komputerze docelowym.  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a>Instalowanie kontrolek Powerpack jako warunek wstępny  
 Aby pomyślnie wdrożyć aplikację, należy wdrożyć wszystkie składniki, które są przywoływane przez aplikację. Proces instalowania wstępnie wymagane składniki są znane jako *uruchamianie*.  
  
 Po zainstalowaniu programu Visual Studio na komputerze deweloperskim, pakiet programu inicjującego Powerpack zostanie dodany do katalogu program inicjujący Instalatora programu Visual Studio. Ten pakiet jest dostępna po wykonaniu procedury dodawania wymagania wstępne dotyczące [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] lub wdrożenia Instalatora Windows.  
  
 Domyślnie uruchomionego składniki są wdrażane w tej samej lokalizacji co pakiet instalacyjny. Alternatywnie można wdrożyć składniki z adresem URL lub plik lokalizację udziału, w którym użytkownicy mogą pobrać je zgodnie z potrzebami.  
  
> [!NOTE]
>  Aby zainstalować składniki uruchomionego, użytkownik może być konieczne użytkownika administracyjnego lub podobne uprawnienia na komputerze. Aby uzyskać [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplikacji, oznacza to, że użytkownik niezbędne są uprawnienia administracyjne do zainstalowania aplikacji, niezależnie od tego, poziom zabezpieczeń, w określonym przez aplikację. Po zainstalowaniu aplikacji użytkownik może uruchomić aplikację bez uprawnień administracyjnych.  
  
 Podczas instalacji użytkownicy otrzymują monit do zainstalowania formantów Powerpack, jeśli nie istnieją na komputerze docelowym.  
  
 Jako alternatywę do uruchomienia można wstępnie wdrożyć formantów Powerpack za pomocą system dystrybucji oprogramowania elektronicznych, takich jak Microsoft Systems Management Server.  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [Visual Basic Powerpacks formantów](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)
