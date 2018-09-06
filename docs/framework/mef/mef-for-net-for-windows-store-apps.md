---
title: MEF dla platformy .NET dla aplikacji Windows Store
ms.date: 03/30/2017
ms.assetid: 7667770e-d163-4ad6-a303-085cf73db2f2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9cb7807fbfc1fbaf039fd7aef04331210dfa7cfa
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777398"
---
# <a name="mef-for-net-for-windows-store-apps"></a><span data-ttu-id="b2a3d-102">MEF dla platformy .NET dla aplikacji Windows Store</span><span class="sxs-lookup"><span data-stu-id="b2a3d-102">MEF for .NET for Windows Store Apps</span></span>
<span data-ttu-id="b2a3d-103"><xref:System.Composition?displayProperty=nameWithType> i jej podrzędne przestrzenie nazw zawierają typy służące do tworzenia extensible [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji za pomocą Managed Extensibility Framework (MEF).</span><span class="sxs-lookup"><span data-stu-id="b2a3d-103"><xref:System.Composition?displayProperty=nameWithType> and its child namespaces contain types for developing extensible [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps with Managed Extensibility Framework (MEF).</span></span> <span data-ttu-id="b2a3d-104">Te przestrzenie nazw są częścią [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] podzbioru dla [!INCLUDE[win8](../../../includes/win8-md.md)] systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="b2a3d-104">These namespaces are part of the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] subset for the [!INCLUDE[win8](../../../includes/win8-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="b2a3d-105">Te przestrzenie nazw nie są częścią biblioteki klas rozpowszechnianej z .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2a3d-105">These namespaces are not part of the core class library distributed with the .NET Framework.</span></span> <span data-ttu-id="b2a3d-106">Aby zainstalować te przestrzenie nazw, otwórz projekt w programie [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], wybierz **Zarządzaj pakietami NuGet** z **projektu** menu, a następnie wyszukaj w trybie online pakiet Microsoft.Composition.</span><span class="sxs-lookup"><span data-stu-id="b2a3d-106">To install these namespaces, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the **Project** menu, and search online for the Microsoft.Composition package.</span></span>  
  
-   <span data-ttu-id="b2a3d-107"><xref:System.Composition?displayProperty=nameWithType> udostępnia klasy, które stanowią podstawę MEF dla [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b2a3d-107"><xref:System.Composition?displayProperty=nameWithType> provides classes that constitute the core MEF for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
-   <span data-ttu-id="b2a3d-108"><xref:System.Composition.Convention?displayProperty=nameWithType> zawiera typy, które obsługują model oparty na Konwencji konfiguracji za pomocą MEF.</span><span class="sxs-lookup"><span data-stu-id="b2a3d-108"><xref:System.Composition.Convention?displayProperty=nameWithType> provides types that support using MEF with a convention-based configuration model.</span></span>  
  
-   <span data-ttu-id="b2a3d-109"><xref:System.Composition.Hosting?displayProperty=nameWithType> zawiera typy MEF, które są przydatne dla deweloperów aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="b2a3d-109"><xref:System.Composition.Hosting?displayProperty=nameWithType> provides MEF types that are useful to developers of host applications.</span></span>  
  
-   <span data-ttu-id="b2a3d-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType> zawiera typy MEF używane wewnętrznie przez aparat kompozycji.</span><span class="sxs-lookup"><span data-stu-id="b2a3d-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType> provides MEF types used internally by the composition engine.</span></span>  
  
 <span data-ttu-id="b2a3d-111">Aby uzyskać więcej informacji na temat [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] i wyświetlić listę przestrzeni nazw i typy, które zawiera, [Omówienie aplikacji .NET dla Windows Store](https://go.microsoft.com/fwlink/p/?LinkID=238312) w Centrum deweloperów Windows.</span><span class="sxs-lookup"><span data-stu-id="b2a3d-111">For more information about [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] and a list of namespaces and types that it contains, see [.NET for Windows Store apps overview](https://go.microsoft.com/fwlink/p/?LinkID=238312) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2a3d-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2a3d-112">See Also</span></span>  
 [<span data-ttu-id="b2a3d-113">Omówienie aplikacji .NET dla Windows Store</span><span class="sxs-lookup"><span data-stu-id="b2a3d-113">.NET for Windows Store apps overview</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=238312)  
 [<span data-ttu-id="b2a3d-114">Aplikacje .NET for Windows Store — obsługiwane interfejsy API</span><span class="sxs-lookup"><span data-stu-id="b2a3d-114">.NET for Windows Store apps – supported APIs</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=247912)  
 [<span data-ttu-id="b2a3d-115">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="b2a3d-115">Managed Extensibility Framework (MEF)</span></span>](../../../docs/framework/mef/index.md)
