---
title: MEF dla platformy .NET dla aplikacji ze Sklepu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7667770e-d163-4ad6-a303-085cf73db2f2
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7f427656f9b385214db5b3bd26c4addb1122b35a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="mef-for-net-for-windows-store-apps"></a><span data-ttu-id="f914d-102">MEF dla platformy .NET dla aplikacji ze Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="f914d-102">MEF for .NET for Windows Store Apps</span></span>
<span data-ttu-id="f914d-103"><xref:System.Composition?displayProperty=nameWithType>i jej podrzędne przestrzenie nazw zawiera typy związane z opracowywaniem extensible [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji z Framework Managed Extensibility (MEF).</span><span class="sxs-lookup"><span data-stu-id="f914d-103"><xref:System.Composition?displayProperty=nameWithType> and its child namespaces contain types for developing extensible [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps with Managed Extensibility Framework (MEF).</span></span> <span data-ttu-id="f914d-104">Te przestrzenie nazw są częścią [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] podzestawu dla [!INCLUDE[win8](../../../includes/win8-md.md)] systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="f914d-104">These namespaces are part of the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] subset for the [!INCLUDE[win8](../../../includes/win8-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="f914d-105">Te obszary nazw nie są częścią podstawowej biblioteki klas rozpowszechnianej za pomocą programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f914d-105">These namespaces are not part of the core class library distributed with the .NET Framework.</span></span> <span data-ttu-id="f914d-106">Aby zainstalować te obszary nazw, otwórz projekt w [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], wybierz **Zarządzaj pakietami NuGet** z **projektu** menu, a następnie wyszukaj w trybie online pakiet Microsoft.Composition.</span><span class="sxs-lookup"><span data-stu-id="f914d-106">To install these namespaces, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the **Project** menu, and search online for the Microsoft.Composition package.</span></span>  
  
-   <span data-ttu-id="f914d-107"><xref:System.Composition?displayProperty=nameWithType>udostępnia klasy, które stanowią podstawę MEF dla [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f914d-107"><xref:System.Composition?displayProperty=nameWithType> provides classes that constitute the core MEF for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
-   <span data-ttu-id="f914d-108"><xref:System.Composition.Convention?displayProperty=nameWithType>zawiera typy, które obsługuje używania MEF z modelu opartych na konwencjach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f914d-108"><xref:System.Composition.Convention?displayProperty=nameWithType> provides types that support using MEF with a convention-based configuration model.</span></span>  
  
-   <span data-ttu-id="f914d-109"><xref:System.Composition.Hosting?displayProperty=nameWithType>zawiera typy MEF, które są przydatne dla deweloperów aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="f914d-109"><xref:System.Composition.Hosting?displayProperty=nameWithType> provides MEF types that are useful to developers of host applications.</span></span>  
  
-   <span data-ttu-id="f914d-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType>zawiera typy MEF używana wewnętrznie przez aparat kompozycji.</span><span class="sxs-lookup"><span data-stu-id="f914d-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType> provides MEF types used internally by the composition engine.</span></span>  
  
 <span data-ttu-id="f914d-111">Aby uzyskać więcej informacji na temat [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] i listę obszary nazw i typy, które zawiera, zobacz [Omówienie aplikacji .NET dla Sklepu Windows](http://go.microsoft.com/fwlink/p/?LinkID=238312) w Centrum deweloperów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f914d-111">For more information about [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] and a list of namespaces and types that it contains, see [.NET for Windows Store apps overview](http://go.microsoft.com/fwlink/p/?LinkID=238312) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f914d-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f914d-112">See Also</span></span>  
 [<span data-ttu-id="f914d-113">Omówienie aplikacji .NET dla Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="f914d-113">.NET for Windows Store apps overview</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=238312)  
 [<span data-ttu-id="f914d-114">.NET dla Sklepu Windows apps — obsługiwanych interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f914d-114">.NET for Windows Store apps – supported APIs</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=247912)  
 [<span data-ttu-id="f914d-115">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="f914d-115">Managed Extensibility Framework (MEF)</span></span>](../../../docs/framework/mef/index.md)
