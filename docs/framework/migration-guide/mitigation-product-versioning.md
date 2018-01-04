---
title: 'Ograniczenie: wersjonowanie produktu'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 15648a3dfc115e55dd78eb1f074b9c4235b89f34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="859b8-102">Ograniczenie: wersjonowanie produktu</span><span class="sxs-lookup"><span data-stu-id="859b8-102">Mitigation: Product Versioning</span></span>
<span data-ttu-id="859b8-103">W [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] i nowszych wersji produktu został zmieniony z poprzednich wersji programu .NET Framework (.NET Framework 4, 4.5.1, 4.5 i 4.5.2).</span><span class="sxs-lookup"><span data-stu-id="859b8-103">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>  
  
## <a name="product-versioning-changes"></a><span data-ttu-id="859b8-104">Zmiany wersji produktu</span><span class="sxs-lookup"><span data-stu-id="859b8-104">Product versioning changes</span></span>  
 <span data-ttu-id="859b8-105">Poniżej przedstawiono szczegółowe zmiany:</span><span class="sxs-lookup"><span data-stu-id="859b8-105">The following are the detailed changes:</span></span>  
  
-   <span data-ttu-id="859b8-106">Wartość `Version` wpis w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klucz został zmieniony na `4.6.` *xxxxx* dla programu .NET Framework 4.6 i zwalnia jego punktu i do `4.7.` *xxxxx* dla. NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="859b8-106">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="859b8-107">W programie .NET Framework 4.5 i 4.5.1, 4.5.2, miał format `4.5.` *xxxxx*.</span><span class="sxs-lookup"><span data-stu-id="859b8-107">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>  
  
-   <span data-ttu-id="859b8-108">Przechowywanie wersji plików i produktu dla plików platformy .NET Framework został zmieniony z wcześniejszych wersji systemu `4.0.30319.x` do `4.6.X.0` dla programu .NET Framework 4.6 i zwalnia jego punktu i do `4.7.X.0` .NET Framework 4.7 i jego punktu wersjami.</span><span class="sxs-lookup"><span data-stu-id="859b8-108">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="859b8-109">Można zobaczyć te nowe wartości, podczas wyświetlania pliku **właściwości** po prawym przyciskiem myszy plik.</span><span class="sxs-lookup"><span data-stu-id="859b8-109">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>  
  
-   <span data-ttu-id="859b8-110"><xref:System.Reflection.AssemblyFileVersionAttribute> i <xref:System.Reflection.AssemblyInformationalVersionAttribute> atrybuty dla zestawów zarządzanych ma <xref:System.Version> wartości w formularzu `4.6.X.0` dla programu .NET Framework 4.6 i jego wersje punktu i `4.7.X.0` dla .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="859b8-110">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>  
  
-   <span data-ttu-id="859b8-111">W [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2 i 4.7, <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwość zwraca ciąg wersji stałej `4.0.30319.42000`.</span><span class="sxs-lookup"><span data-stu-id="859b8-111">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2, and 4.7, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="859b8-112">W programie .NET Framework 4, 4.5.1, 4.5 i 4.5.2, zwraca ciągów w formacie `4.0.30319.xxxxx` (na przykład "4.0.30319.18010").</span><span class="sxs-lookup"><span data-stu-id="859b8-112">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="859b8-113">Należy pamiętać, że nie zaleca się kod aplikacji, biorąc wszelkie nowe zależności <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="859b8-113">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>  
  
### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="859b8-114">Obsługa zmiany wersji produktu</span><span class="sxs-lookup"><span data-stu-id="859b8-114">Handling the product versioning changes</span></span>  
 <span data-ttu-id="859b8-115">Ogólnie rzecz biorąc aplikacje powinny zależą od zalecane techniki wykrywania czynności, takich jak wersja środowiska uruchomieniowego .NET Framework i katalog instalacji:</span><span class="sxs-lookup"><span data-stu-id="859b8-115">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>  
  
-   <span data-ttu-id="859b8-116">Aby wykryć wersji środowiska uruchomieniowego .NET Framework, zobacz [porady: ustalić, które .NET Framework są zainstalowane wersje](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="859b8-116">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>  
  
-   <span data-ttu-id="859b8-117">Aby określić ścieżkę instalacji dla programu .NET Framework, użyj wartości `InstallPath` wpis w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klucza.</span><span class="sxs-lookup"><span data-stu-id="859b8-117">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="859b8-118">Nazwa podklucza jest `NET Framework Setup`, a nie `.NET Framework Setup`.</span><span class="sxs-lookup"><span data-stu-id="859b8-118">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>  
  
-   <span data-ttu-id="859b8-119">Aby określić ścieżkę katalogu do .NET Framework środowisko uruchomieniowe języka wspólnego, należy wywołać <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="859b8-119">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="859b8-120">Aby pobrać wersji środowiska CLR, należy wywołać <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="859b8-120">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="859b8-121">Dla programu .NET Framework 4 i jego punktu zwalnia (.NET Framework 4.5, 4.5.1, 4.5.2, i [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2 i 4.7), zwraca ciąg `v4.0.30319`.</span><span class="sxs-lookup"><span data-stu-id="859b8-121">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="859b8-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="859b8-122">See Also</span></span>  
 [<span data-ttu-id="859b8-123">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="859b8-123">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
 
