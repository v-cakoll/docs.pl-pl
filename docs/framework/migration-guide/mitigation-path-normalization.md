---
title: "Ograniczenie: Ścieżka normalizacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e30099e315f88bd051dca2e1f6c83d1bccc49569
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="bedbc-102">Ograniczenie: Ścieżka normalizacji</span><span class="sxs-lookup"><span data-stu-id="bedbc-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="bedbc-103">Począwszy od aplikacji docelowej [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], zmienił ścieżkę normalizacji w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bedbc-103">Starting with apps the target  the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="bedbc-104">Co to jest ścieżka normalizacji?</span><span class="sxs-lookup"><span data-stu-id="bedbc-104">What is path normalization?</span></span>  
 <span data-ttu-id="bedbc-105">Normalizacji ścieżki pociąga za sobą modyfikowanie ciąg, który określa ścieżkę lub plików, dzięki czemu odpowiada prawidłową ścieżkę na docelowy system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="bedbc-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="bedbc-106">Normalizacji zwykle obejmuje:</span><span class="sxs-lookup"><span data-stu-id="bedbc-106">Normalization typically involves:</span></span>  
  
-   <span data-ttu-id="bedbc-107">Kanoniczną separatory składnika i katalogu.</span><span class="sxs-lookup"><span data-stu-id="bedbc-107">Canonicalizing component and directory separators.</span></span>  
  
-   <span data-ttu-id="bedbc-108">Stosowanie bieżący katalog do ścieżki względnej.</span><span class="sxs-lookup"><span data-stu-id="bedbc-108">Applying the current directory to a relative path.</span></span>  
  
-   <span data-ttu-id="bedbc-109">Ocena względna katalogu (`.`) lub katalogu nadrzędnego (`..`) w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="bedbc-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
-   <span data-ttu-id="bedbc-110">Przycinanie określonych znaków.</span><span class="sxs-lookup"><span data-stu-id="bedbc-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="bedbc-111">Zmiany</span><span class="sxs-lookup"><span data-stu-id="bedbc-111">The changes</span></span>  
 <span data-ttu-id="bedbc-112">Począwszy od aplikacji przeznaczonych [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], zmienił ścieżkę normalizacji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bedbc-112">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization has changed in the following ways:</span></span>  
  
-   <span data-ttu-id="bedbc-113">Środowisko uruchomieniowe różni się do systemu operacyjnego [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963\(v=vs.85\).aspx) funkcji normalizacji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="bedbc-113">The runtime defers to the operating system's [GetFullPathName](https://msdn.microsoft.com/library/windows/desktop/aa364963\(v=vs.85\).aspx) function to normalize paths.</span></span>  
  
-   <span data-ttu-id="bedbc-114">Normalizacji nie obejmuje przycinanie końca katalogu segmenty (na przykład miejsca na końcu nazwy katalogu).</span><span class="sxs-lookup"><span data-stu-id="bedbc-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
-   <span data-ttu-id="bedbc-115">Obsługa składnia ścieżki urządzenia w trybie pełnego zaufania, w tym `\\.\` i dla interfejsów API We/Wy plików w bibliotece mscorlib.dll, `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="bedbc-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
-   <span data-ttu-id="bedbc-116">Środowisko uruchomieniowe nie można zweryfikować ścieżki składni urządzeń.</span><span class="sxs-lookup"><span data-stu-id="bedbc-116">The runtime does not validate device syntax paths.</span></span>  
  
-   <span data-ttu-id="bedbc-117">Użycie składni urządzenia do dostępu alternatywne strumienie danych jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="bedbc-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="bedbc-118">Wpływ</span><span class="sxs-lookup"><span data-stu-id="bedbc-118">Impact</span></span>  
 <span data-ttu-id="bedbc-119">W przypadku aplikacji, które odnoszą się do [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] lub później, zmiany te są domyślnie.</span><span class="sxs-lookup"><span data-stu-id="bedbc-119">For apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later, these changes are on  by default.</span></span> <span data-ttu-id="bedbc-120">Powinny one zwiększyć wydajność zezwalając metod dostępu wcześniej niedostępny ścieżki do.</span><span class="sxs-lookup"><span data-stu-id="bedbc-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
 <span data-ttu-id="bedbc-121">Aplikacje, które odnoszą się do [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] i wcześniejszych wersji, ale są uruchomione w [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] lub nowszy nie ma wpływu na tę zmianę.</span><span class="sxs-lookup"><span data-stu-id="bedbc-121">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions but are running under the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="bedbc-122">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="bedbc-122">Mitigation</span></span>  
 <span data-ttu-id="bedbc-123">Aplikacje, które odnoszą się do [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] lub nowszym można zrezygnować z tej zmiany i użyć starszego normalizacji, dodając następujące polecenie, aby [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="bedbc-123">Apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
 <span data-ttu-id="bedbc-124">Aplikacje, które odnoszą się do [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] lub wcześniej, ale są uruchomione na [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] lub nowszym można włączyć zmiany ścieżki normalizacji, dodając następujący wiersz do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) części aplikacji. plik konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="bedbc-124">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] or earlier but are running on the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bedbc-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bedbc-125">See Also</span></span>  
 [<span data-ttu-id="bedbc-126">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="bedbc-126">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
