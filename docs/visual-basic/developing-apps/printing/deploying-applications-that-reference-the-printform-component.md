---
title: Wdrażanie aplikacji, które odwołują się do wyniku składnik PrintForm (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
ms.openlocfilehash: 6384ad6e3bf0520362267eddc8f7bbb05b37f283
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400429"
---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a>Wdrażanie aplikacji, które odwołują się do wyniku składnik PrintForm (Visual Basic)
Jeśli chcesz wdrożyć aplikację, która odwołuje się <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnik składnika musi być zainstalowany na komputerze docelowym.  
  
 Formantów PowerPack znajdują się już w programie Visual Studio, ale można je pobrać [Centrum pobierania](https://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="installing-the-printform-as-a-prerequisite"></a>Instalowanie PrintForm jako warunek wstępny  
 Aby pomyślnie wdrożyć aplikację, należy wdrożyć wszystkie składniki, które są przywoływane przez aplikację. Proces instalowania wstępnie wymagane składniki są znane jako *uruchamianie*.  
  
 Gdy <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnik jest zainstalowany na komputerze deweloperskim, program inicjujący programu Microsoft Visual Basic Power Packs zostanie dodany do katalogu program inicjujący Instalatora programu Visual Studio. Ten pakiet jest dostępna po wykonaniu procedury dodawania wymagania wstępne dotyczące [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] lub wdrożenia Instalatora Windows.  
  
 Domyślnie uruchomionego składniki są wdrażane w tej samej lokalizacji co pakiet instalacyjny. Alternatywnie można wdrożyć składniki z adresem URL lub plik lokalizację udziału, w którym użytkownicy mogą pobrać je zgodnie z potrzebami.  
  
> [!NOTE]
>  Aby zainstalować składniki uruchomionego, użytkownik może być konieczne użytkownika administracyjnego lub podobne uprawnienia na komputerze. Aby uzyskać [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplikacji, oznacza to, że użytkownik niezbędne są uprawnienia administracyjne do zainstalowania aplikacji, niezależnie od tego, poziom zabezpieczeń, w określonym przez aplikację. Po zainstalowaniu aplikacji użytkownik może uruchomić aplikację bez uprawnień administracyjnych.  
  
 Podczas instalacji użytkownicy otrzymują monit do zainstalowania <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnik, jeśli nie ma go na komputerze docelowym.  
  
 Alternatywą do uruchomienia przed wdrożeniem <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> składnika za pomocą systemu dystrybucji oprogramowania elektronicznych, takich jak Microsoft Systems Management Server.  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [Składnik PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)
