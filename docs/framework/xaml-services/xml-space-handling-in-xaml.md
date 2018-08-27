---
title: xml:space — Obsługa w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 051cb6b3a314509e9593ee570fd659098670e88b
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925860"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="1e47c-102">xml:space — Obsługa w XAML</span><span class="sxs-lookup"><span data-stu-id="1e47c-102">xml:space Handling in XAML</span></span>
<span data-ttu-id="1e47c-103">`xml:space` Atrybut jest definiowany w języku XML atrybut deklarujący zachowanie przetwarzania odstępu w obrębie elementu obiektu.</span><span class="sxs-lookup"><span data-stu-id="1e47c-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="1e47c-104">To zachowanie jest odpowiednie dla całej zawartości (tekst wewnętrzny) zawartych w elemencie gdzie `xml:space` jest zadeklarowana, a także zakresów do elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="1e47c-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="1e47c-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="1e47c-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 <span data-ttu-id="1e47c-106">\- lub —</span><span class="sxs-lookup"><span data-stu-id="1e47c-106">\- or -</span></span>  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a><span data-ttu-id="1e47c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1e47c-107">Remarks</span></span>  
 <span data-ttu-id="1e47c-108">Definicja `xml:space` atrybut w XAML, łącznie z jego dwóch wartości jest tworzony na podstawie `xml:space` zgodnie z definicją jako "specjalne atrybutu" specyfikacje W3C XML.</span><span class="sxs-lookup"><span data-stu-id="1e47c-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>  
  
 <span data-ttu-id="1e47c-109">Wartość domyślna `xml:space` atrybut jest wartość literału `"default"`.</span><span class="sxs-lookup"><span data-stu-id="1e47c-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="1e47c-110">Dla wartości `"default"`, lub jeśli `xml:space` nie wskazano, zachowanie analizowania znaczące odstępu jest domyślna obsługa, zgodnie z definicją w temacie [spacji w XAML na przetworzenie](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="1e47c-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span></span>  
  
 <span data-ttu-id="1e47c-111">Aby zachować biały znak w zawartości elementu obiektu, należy określić `xml:space="preserve"` w elemencie tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1e47c-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>  
  
 <span data-ttu-id="1e47c-112">W większości interpretacji `xml:space` efekty atrybutem i wartością atrybutu są ograniczone do elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="1e47c-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>  
  
 <span data-ttu-id="1e47c-113">Wyczerpujące omówienie odstępu, przetwarzanie w XAML, zobacz [spacji w XAML na przetworzenie](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="1e47c-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e47c-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1e47c-114">See Also</span></span>  
 [<span data-ttu-id="1e47c-115">Znak odstępu przetwarzanie w XAML</span><span class="sxs-lookup"><span data-stu-id="1e47c-115">White-space processing in XAML</span></span>](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)  
 [<span data-ttu-id="1e47c-116">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="1e47c-116">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
