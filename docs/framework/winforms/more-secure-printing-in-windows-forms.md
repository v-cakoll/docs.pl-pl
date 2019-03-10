---
title: Bezpieczniejsze drukowanie w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
ms.openlocfilehash: 2fd61ea1c56ee2dbe7ff725d9f9f79df6b6cdfd8
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723049"
---
# <a name="more-secure-printing-in-windows-forms"></a>Bezpieczniejsze drukowanie w formularzach systemu Windows
Aplikacje Windows Forms często zawierają możliwości drukowania. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Używa <xref:System.Drawing.Printing.PrintingPermission> klasy, aby kontrolować dostęp do możliwości drukowania oraz skojarzonych z nimi <xref:System.Drawing.Printing.PrintingPermissionLevel> wartości wyliczenia, aby wskazać poziom dostępu. Domyślnie program drukowania jest domyślnie włączone w strefy Lokalny Intranet i Internet poziom dostępu jest jednak ograniczone obie strefy. Czy aplikację można wydrukować, wymaga interakcji z użytkownikiem lub nie wydruku zależy od wartości uprawnienia nadane aplikacji. Domyślnie, otrzymuje lokalnej strefy intranetowej <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> otrzymuje dostęp i w strefie intranetowej <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> dostępu.  
  
 W poniższej tabeli przedstawiono funkcje dostępne na każdym drukowaniem poziomie uprawnień.  
  
|PrintingPermissionLevel|Opis|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|Zapewnia pełny dostęp do wszystkich zainstalowanych drukarek.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|Umożliwia programowe zostanie użyta drukarka domyślna bezpieczniejsze drukowaniem i za pomocą restrykcyjne okna dialogowego drukowania. <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> jest podzbiorem <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|Umożliwia drukowanie tylko z okna dialogowego z ograniczeniami więcej. <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> jest podzbiorem <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|Uniemożliwia dostęp do drukarki. <xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> jest podzbiorem <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.|  
  
## <a name="see-also"></a>Zobacz także
- [Bezpieczniejszy dostęp do plików i danych w formularzach Windows Forms](more-secure-file-and-data-access-in-windows-forms.md)
- [Dodatkowe zagadnienia z zakresu zabezpieczeń dotyczące formularzy Windows Forms](additional-security-considerations-in-windows-forms.md)
- [Przegląd zabezpieczeń w formularzach Windows Forms](security-in-windows-forms-overview.md)
- [Zabezpieczenia formularzy Windows Forms](windows-forms-security.md)
