---
title: Bezpieczniejsze drukowanie
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
ms.openlocfilehash: 6285b76d01660bfa761ea606421f264bdc0c0af5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734882"
---
# <a name="more-secure-printing-in-windows-forms"></a>Bezpieczniejsze drukowanie w formularzach systemu Windows
Aplikacje Windows Forms często obejmują możliwości drukowania. .NET Framework używa klasy <xref:System.Drawing.Printing.PrintingPermission> do kontrolowania dostępu do możliwości drukowania i skojarzonej wartości wyliczenia <xref:System.Drawing.Printing.PrintingPermissionLevel> w celu wskazania poziomu dostępu. Domyślnie drukowanie jest domyślnie włączone w lokalnym intranecie i strefach internetowych. Jednak poziom dostępu jest ograniczony w obu strefach. Czy aplikacja może drukować, wymaga interakcji z użytkownikiem lub nie można drukować zależnie od wartości uprawnienia udzielonej aplikacji. Domyślnie strefa Lokalny intranet otrzymuje <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> dostępu, a strefa intranetowa otrzymuje <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> dostęp.  
  
 W poniższej tabeli przedstawiono funkcje dostępne na każdym poziomie uprawnień do drukowania.  
  
|Się|Opis|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|Zapewnia pełny dostęp do wszystkich zainstalowanych drukarek.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|Umożliwia programistyczne drukowanie na drukarce domyślnej i bezpieczniejsze Drukowanie przy użyciu ograniczonego okna dialogowego drukowania. <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> jest podzbiorem <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|Umożliwia drukowanie tylko z okna dialogowego o większej liczbie ograniczeń. <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> jest podzbiorem <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|Uniemożliwia dostęp do drukarek. <xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> jest podzbiorem <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.|  
  
## <a name="see-also"></a>Zobacz także

- [Bezpieczniejszy dostęp do plików i danych w formularzach Windows Forms](more-secure-file-and-data-access-in-windows-forms.md)
- [Dodatkowe zagadnienia z zakresu zabezpieczeń dotyczące formularzy Windows Forms](additional-security-considerations-in-windows-forms.md)
- [Przegląd zabezpieczeń w formularzach Windows Forms](security-in-windows-forms-overview.md)
- [Zabezpieczenia formularzy Windows Forms](windows-forms-security.md)
