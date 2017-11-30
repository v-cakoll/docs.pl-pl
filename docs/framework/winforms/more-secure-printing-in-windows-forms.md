---
title: Bezpieczniejsze drukowanie w formularzach systemu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, printing
- PrintingPermission class [Windows Forms], Windows Forms security
- printing [Windows Forms], security
- security [Windows Forms], printing
ms.assetid: 48fd36ac-872f-4de0-902a-e52969cd4367
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b89a94fd0223d817b0dee37f7a3ed84dcbacbbec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="more-secure-printing-in-windows-forms"></a>Bezpieczniejsze drukowanie w formularzach systemu Windows
Aplikacje Windows Forms często zawierają możliwości drukowania. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Używa <xref:System.Drawing.Printing.PrintingPermission> klasę, aby kontrolować dostęp do możliwości drukowania oraz skojarzonych z nimi <xref:System.Drawing.Printing.PrintingPermissionLevel> wartość wyliczenia wskazująca poziom dostępu. Domyślnie drukowanie jest domyślnie włączone w strefach Lokalny Intranet i Internet jednak poziom dostępu jest ograniczona w obu strefy. Czy aplikacja może drukować, wymaga interakcji użytkownika, lub nie wydruku zależy od wartości uprawnienia przyznane aplikacji. Domyślnie odbiera lokalnej strefy intranetowej <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> dostępu i strefy Intranet odbiera <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> dostępu.  
  
 W poniższej tabeli przedstawiono funkcje dostępne na każdym poziomie drukowania uprawnień.  
  
|PrintingPermissionLevel|Opis|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|Zapewnia pełny dostęp do wszystkich zainstalowanych drukarek.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|Umożliwia drukowanie programowe używają domyślnej drukarki i bezpieczniejsze drukowanie za pomocą restrykcyjne okna dialogowego drukowania. <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>jest ona podzbiorem <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|Udostępnia drukowanie tylko z ograniczonej inne okno dialogowe. <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>jest ona podzbiorem <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|Uniemożliwia dostęp do drukarki. <xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>jest ona podzbiorem <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.|  
  
## <a name="see-also"></a>Zobacz też  
 [Plik bezpieczniejsze i dostęp do danych w formularzach systemu Windows](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [Zagadnienia dotyczące zabezpieczeń w formularzach systemu Windows](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [Zabezpieczenia w formularzach systemu Windows-omówienie](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [Zabezpieczenia formularzy systemu Windows](../../../docs/framework/winforms/windows-forms-security.md)
