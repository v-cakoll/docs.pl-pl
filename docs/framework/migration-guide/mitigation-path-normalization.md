---
title: 'Ograniczenie: Ścieżka normalizacji'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa31641cc325f15b9afe677038deb33c57e77fd1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508816"
---
# <a name="mitigation-path-normalization"></a><span data-ttu-id="f100f-102">Ograniczenie: Ścieżka normalizacji</span><span class="sxs-lookup"><span data-stu-id="f100f-102">Mitigation: Path Normalization</span></span>
<span data-ttu-id="f100f-103">Począwszy od aplikacji docelowej [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], zmienił ścieżkę normalizacji w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f100f-103">Starting with apps the target  the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization in the .NET Framework has changed.</span></span>  
  
## <a name="what-is-path-normalization"></a><span data-ttu-id="f100f-104">Co to jest ścieżka normalizacji?</span><span class="sxs-lookup"><span data-stu-id="f100f-104">What is path normalization?</span></span>  
 <span data-ttu-id="f100f-105">Normalizowanie ścieżką obejmuje modyfikuje ciąg, który identyfikuje pliku lub ścieżki, tak aby odpowiada prawidłowej ścieżki, na docelowy system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="f100f-105">Normalizing a path involves modifying the string that identifies a path or file so that it conforms to a valid path on the target operating system.</span></span> <span data-ttu-id="f100f-106">Normalizacja zwykle obejmuje:</span><span class="sxs-lookup"><span data-stu-id="f100f-106">Normalization typically involves:</span></span>  
  
-   <span data-ttu-id="f100f-107">Przekształcania w formę kanoniczną separatory składnika i katalog.</span><span class="sxs-lookup"><span data-stu-id="f100f-107">Canonicalizing component and directory separators.</span></span>  
  
-   <span data-ttu-id="f100f-108">Stosowanie bieżący katalog do ścieżki względnej.</span><span class="sxs-lookup"><span data-stu-id="f100f-108">Applying the current directory to a relative path.</span></span>  
  
-   <span data-ttu-id="f100f-109">Ocena względna katalogu (`.`) lub katalogu nadrzędnego (`..`) w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="f100f-109">Evaluating the relative directory (`.`) or the parent directory (`..`) in a path.</span></span>  
  
-   <span data-ttu-id="f100f-110">Przycinanie określonych znaków.</span><span class="sxs-lookup"><span data-stu-id="f100f-110">Trimming specified characters.</span></span>  
  
## <a name="the-changes"></a><span data-ttu-id="f100f-111">Zmiany</span><span class="sxs-lookup"><span data-stu-id="f100f-111">The changes</span></span>  
 <span data-ttu-id="f100f-112">Począwszy od aplikacji, których platformą docelową [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], zmienił ścieżkę normalizacji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f100f-112">Starting with apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], path normalization has changed in the following ways:</span></span>  
  
-   <span data-ttu-id="f100f-113">Środowisko uruchomieniowe różni się w systemie operacyjnym [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) funkcję, aby znormalizować ścieżki.</span><span class="sxs-lookup"><span data-stu-id="f100f-113">The runtime defers to the operating system's [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) function to normalize paths.</span></span>  
  
-   <span data-ttu-id="f100f-114">Nie jest już normalizacji obejmuje przycinania koniec segmentów katalogu (np. miejsce na końcu nazwy katalogu).</span><span class="sxs-lookup"><span data-stu-id="f100f-114">Normalization no longer involves trimming the end of directory segments (such as a space at the end of a directory name).</span></span>  
  
-   <span data-ttu-id="f100f-115">Obsługa składnia ścieżki urządzenia w trybie pełnego zaufania, w tym `\\.\` a w przypadku plikowych interfejsów API we/wy w mscorlib.dll, `\\?\`.</span><span class="sxs-lookup"><span data-stu-id="f100f-115">Support for device path syntax in full trust, including  `\\.\` and, for file I/O APIs   in mscorlib.dll, `\\?\`.</span></span>  
  
-   <span data-ttu-id="f100f-116">Środowisko wykonawcze nie można zweryfikować ścieżki składni urządzeń.</span><span class="sxs-lookup"><span data-stu-id="f100f-116">The runtime does not validate device syntax paths.</span></span>  
  
-   <span data-ttu-id="f100f-117">Użycie składni urządzenia do uzyskania dostępu alternatywne strumienie danych jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f100f-117">The use of device syntax to access alternate data streams is supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="f100f-118">Wpływ</span><span class="sxs-lookup"><span data-stu-id="f100f-118">Impact</span></span>  
 <span data-ttu-id="f100f-119">W przypadku aplikacji, których platformą docelową [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] lub nowszym, te zmiany są domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="f100f-119">For apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later, these changes are on  by default.</span></span> <span data-ttu-id="f100f-120">One należy poprawić wydajność podczas gdy metody dostępu do ścieżki niedostępnych wcześniej.</span><span class="sxs-lookup"><span data-stu-id="f100f-120">They should improve performance while allowing methods to access previously inaccessible paths.</span></span>  
  
 <span data-ttu-id="f100f-121">Aplikacje, których platformą docelową [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] i wcześniejszymi wersjami, ale nie są uruchomione w ramach [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] lub nowszej nie ma wpływu na tę zmianę.</span><span class="sxs-lookup"><span data-stu-id="f100f-121">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and earlier versions but are running under the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later are unaffected by this change.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="f100f-122">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="f100f-122">Mitigation</span></span>  
 <span data-ttu-id="f100f-123">Aplikacje, których platformą docelową [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] lub nowszym można zrezygnować z tej zmiany i użyć starszego normalizacji, dodając następujące polecenie, aby [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcję pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="f100f-123">Apps that target the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can opt out of this change and use legacy normalization by adding the following to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
 <span data-ttu-id="f100f-124">Aplikacje, których platformą docelową [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] lub wcześniej, ale są uruchomione na [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] lub nowszym można włączyć zmiany ścieżki normalizacji, dodając następujący wiersz do [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) części aplikacji. plik konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="f100f-124">Apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] or earlier but are running on the [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] or later can enable the changes to path normalization by adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the application .configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f100f-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f100f-125">See Also</span></span>  
 [<span data-ttu-id="f100f-126">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="f100f-126">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
