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
# <a name="more-secure-printing-in-windows-forms"></a><span data-ttu-id="16b0b-102">Bezpieczniejsze drukowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="16b0b-102">More Secure Printing in Windows Forms</span></span>
<span data-ttu-id="16b0b-103">Aplikacje Windows Forms często zawierają możliwości drukowania.</span><span class="sxs-lookup"><span data-stu-id="16b0b-103">Windows Forms applications frequently include printing abilities.</span></span> <span data-ttu-id="16b0b-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Używa <xref:System.Drawing.Printing.PrintingPermission> klasę, aby kontrolować dostęp do możliwości drukowania oraz skojarzonych z nimi <xref:System.Drawing.Printing.PrintingPermissionLevel> wartość wyliczenia wskazująca poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="16b0b-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uses the <xref:System.Drawing.Printing.PrintingPermission> class to control access to printing capabilities and the associated <xref:System.Drawing.Printing.PrintingPermissionLevel> enumeration value to indicate the level of access.</span></span> <span data-ttu-id="16b0b-105">Domyślnie drukowanie jest domyślnie włączone w strefach Lokalny Intranet i Internet jednak poziom dostępu jest ograniczona w obu strefy.</span><span class="sxs-lookup"><span data-stu-id="16b0b-105">By default, printing is enabled by default in the Local Intranet and Internet zones; however, the level of access is restricted in both zones.</span></span> <span data-ttu-id="16b0b-106">Czy aplikacja może drukować, wymaga interakcji użytkownika, lub nie wydruku zależy od wartości uprawnienia przyznane aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16b0b-106">Whether your application can print, requires user interaction, or cannot print depends upon the permission value granted to the application.</span></span> <span data-ttu-id="16b0b-107">Domyślnie odbiera lokalnej strefy intranetowej <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> dostępu i strefy Intranet odbiera <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> dostępu.</span><span class="sxs-lookup"><span data-stu-id="16b0b-107">By default, the Local Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> access and the Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> access.</span></span>  
  
 <span data-ttu-id="16b0b-108">W poniższej tabeli przedstawiono funkcje dostępne na każdym poziomie drukowania uprawnień.</span><span class="sxs-lookup"><span data-stu-id="16b0b-108">The following table shows the functionality available at each printing permission level.</span></span>  
  
|<span data-ttu-id="16b0b-109">PrintingPermissionLevel</span><span class="sxs-lookup"><span data-stu-id="16b0b-109">PrintingPermissionLevel</span></span>|<span data-ttu-id="16b0b-110">Opis</span><span class="sxs-lookup"><span data-stu-id="16b0b-110">Description</span></span>|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|<span data-ttu-id="16b0b-111">Zapewnia pełny dostęp do wszystkich zainstalowanych drukarek.</span><span class="sxs-lookup"><span data-stu-id="16b0b-111">Provides full access to all installed printers.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|<span data-ttu-id="16b0b-112">Umożliwia drukowanie programowe używają domyślnej drukarki i bezpieczniejsze drukowanie za pomocą restrykcyjne okna dialogowego drukowania.</span><span class="sxs-lookup"><span data-stu-id="16b0b-112">Enables programmatic printing to the default printer and safer printing through a restrictive printing dialog box.</span></span> <span data-ttu-id="16b0b-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>jest ona podzbiorem <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span><span class="sxs-lookup"><span data-stu-id="16b0b-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|<span data-ttu-id="16b0b-114">Udostępnia drukowanie tylko z ograniczonej inne okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="16b0b-114">Provides printing only from a more-restricted dialog box.</span></span> <span data-ttu-id="16b0b-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>jest ona podzbiorem <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span><span class="sxs-lookup"><span data-stu-id="16b0b-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|<span data-ttu-id="16b0b-116">Uniemożliwia dostęp do drukarki.</span><span class="sxs-lookup"><span data-stu-id="16b0b-116">Prevents access to printers.</span></span> <span data-ttu-id="16b0b-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>jest ona podzbiorem <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span><span class="sxs-lookup"><span data-stu-id="16b0b-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="16b0b-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16b0b-118">See Also</span></span>  
 [<span data-ttu-id="16b0b-119">Plik bezpieczniejsze i dostęp do danych w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="16b0b-119">More Secure File and Data Access in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [<span data-ttu-id="16b0b-120">Zagadnienia dotyczące zabezpieczeń w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="16b0b-120">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [<span data-ttu-id="16b0b-121">Zabezpieczenia w formularzach systemu Windows-omówienie</span><span class="sxs-lookup"><span data-stu-id="16b0b-121">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [<span data-ttu-id="16b0b-122">Zabezpieczenia formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="16b0b-122">Windows Forms Security</span></span>](../../../docs/framework/winforms/windows-forms-security.md)
