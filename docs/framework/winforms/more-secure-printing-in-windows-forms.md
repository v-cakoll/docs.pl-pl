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
ms.workload: dotnet
ms.openlocfilehash: 1f36ee150e4dcca74141b644a55451abd4a4fd21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="more-secure-printing-in-windows-forms"></a><span data-ttu-id="57d83-102">Bezpieczniejsze drukowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="57d83-102">More Secure Printing in Windows Forms</span></span>
<span data-ttu-id="57d83-103">Aplikacje Windows Forms często zawierają możliwości drukowania.</span><span class="sxs-lookup"><span data-stu-id="57d83-103">Windows Forms applications frequently include printing abilities.</span></span> <span data-ttu-id="57d83-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Używa <xref:System.Drawing.Printing.PrintingPermission> klasę, aby kontrolować dostęp do możliwości drukowania oraz skojarzonych z nimi <xref:System.Drawing.Printing.PrintingPermissionLevel> wartość wyliczenia wskazująca poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="57d83-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uses the <xref:System.Drawing.Printing.PrintingPermission> class to control access to printing capabilities and the associated <xref:System.Drawing.Printing.PrintingPermissionLevel> enumeration value to indicate the level of access.</span></span> <span data-ttu-id="57d83-105">Domyślnie drukowanie jest domyślnie włączone w strefach Lokalny Intranet i Internet jednak poziom dostępu jest ograniczona w obu strefy.</span><span class="sxs-lookup"><span data-stu-id="57d83-105">By default, printing is enabled by default in the Local Intranet and Internet zones; however, the level of access is restricted in both zones.</span></span> <span data-ttu-id="57d83-106">Czy aplikacja może drukować, wymaga interakcji użytkownika, lub nie wydruku zależy od wartości uprawnienia przyznane aplikacji.</span><span class="sxs-lookup"><span data-stu-id="57d83-106">Whether your application can print, requires user interaction, or cannot print depends upon the permission value granted to the application.</span></span> <span data-ttu-id="57d83-107">Domyślnie odbiera lokalnej strefy intranetowej <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> dostępu i strefy Intranet odbiera <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> dostępu.</span><span class="sxs-lookup"><span data-stu-id="57d83-107">By default, the Local Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> access and the Intranet zone receives <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> access.</span></span>  
  
 <span data-ttu-id="57d83-108">W poniższej tabeli przedstawiono funkcje dostępne na każdym poziomie drukowania uprawnień.</span><span class="sxs-lookup"><span data-stu-id="57d83-108">The following table shows the functionality available at each printing permission level.</span></span>  
  
|<span data-ttu-id="57d83-109">PrintingPermissionLevel</span><span class="sxs-lookup"><span data-stu-id="57d83-109">PrintingPermissionLevel</span></span>|<span data-ttu-id="57d83-110">Opis</span><span class="sxs-lookup"><span data-stu-id="57d83-110">Description</span></span>|  
|-----------------------------|-----------------|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>|<span data-ttu-id="57d83-111">Zapewnia pełny dostęp do wszystkich zainstalowanych drukarek.</span><span class="sxs-lookup"><span data-stu-id="57d83-111">Provides full access to all installed printers.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>|<span data-ttu-id="57d83-112">Umożliwia drukowanie programowe używają domyślnej drukarki i bezpieczniejsze drukowanie za pomocą restrykcyjne okna dialogowego drukowania.</span><span class="sxs-lookup"><span data-stu-id="57d83-112">Enables programmatic printing to the default printer and safer printing through a restrictive printing dialog box.</span></span> <span data-ttu-id="57d83-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>jest ona podzbiorem <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span><span class="sxs-lookup"><span data-stu-id="57d83-113"><xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.AllPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>|<span data-ttu-id="57d83-114">Udostępnia drukowanie tylko z ograniczonej inne okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="57d83-114">Provides printing only from a more-restricted dialog box.</span></span> <span data-ttu-id="57d83-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>jest ona podzbiorem <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span><span class="sxs-lookup"><span data-stu-id="57d83-115"><xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.DefaultPrinting>.</span></span>|  
|<xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>|<span data-ttu-id="57d83-116">Uniemożliwia dostęp do drukarki.</span><span class="sxs-lookup"><span data-stu-id="57d83-116">Prevents access to printers.</span></span> <span data-ttu-id="57d83-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting>jest ona podzbiorem <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span><span class="sxs-lookup"><span data-stu-id="57d83-117"><xref:System.Drawing.Printing.PrintingPermissionLevel.NoPrinting> is a subset of <xref:System.Drawing.Printing.PrintingPermissionLevel.SafePrinting>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57d83-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57d83-118">See Also</span></span>  
 [<span data-ttu-id="57d83-119">Bezpieczniejszy dostęp do plików i danych w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="57d83-119">More Secure File and Data Access in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 [<span data-ttu-id="57d83-120">Dodatkowe zagadnienia z zakresu zabezpieczeń dotyczące formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="57d83-120">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [<span data-ttu-id="57d83-121">Przegląd zabezpieczeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="57d83-121">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [<span data-ttu-id="57d83-122">Zabezpieczenia formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="57d83-122">Windows Forms Security</span></span>](../../../docs/framework/winforms/windows-forms-security.md)
