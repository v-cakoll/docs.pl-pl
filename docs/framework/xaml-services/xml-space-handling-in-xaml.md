---
title: "xml:space — Obsługa w XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], whitespace processing
- xml:space attribute [XAML Services]
- whitespace processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
caps.latest.revision: "15"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a5048cbad1d2ea914d041ac3c87a43223b208c3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="5d14e-102">xml:space — Obsługa w XAML</span><span class="sxs-lookup"><span data-stu-id="5d14e-102">xml:space Handling in XAML</span></span>
<span data-ttu-id="5d14e-103">`xml:space` Atrybut jest definiowany w języku XML atrybut deklarujący zachowania przetwarzania znaczącym odstępem w elemencie obiektu.</span><span class="sxs-lookup"><span data-stu-id="5d14e-103">The `xml:space` attribute is an XML-defined attribute that declares the significant whitespace processing behavior within an object element.</span></span> <span data-ttu-id="5d14e-104">To zachowanie jest odpowiednie dla całej zawartości (tekst wewnętrzny) zawartych w elemencie gdzie `xml:space` jest zadeklarowana, a także zakresów do elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="5d14e-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="5d14e-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="5d14e-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 <span data-ttu-id="5d14e-106">\-lub -</span><span class="sxs-lookup"><span data-stu-id="5d14e-106">\- or -</span></span>  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a><span data-ttu-id="5d14e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d14e-107">Remarks</span></span>  
 <span data-ttu-id="5d14e-108">Definicja `xml:space` atrybut w XAML, łącznie z jej dwa możliwe wartości jest pochodną `xml:space` zgodnie z definicją jako "specjalne atrybutu" specyfikacje W3C XML.</span><span class="sxs-lookup"><span data-stu-id="5d14e-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>  
  
 <span data-ttu-id="5d14e-109">Wartość domyślna `xml:space` atrybut jest wartość literału `"default"`.</span><span class="sxs-lookup"><span data-stu-id="5d14e-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="5d14e-110">Wartość `"default"`, lub jeśli `xml:space` nie wskazano, zachowanie podczas analizowania znaczące światła jest domyślna obsługa, zgodnie z definicją w temacie [przetwarzanie spacji w XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="5d14e-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant whitespace parsing is the default handling, as defined in the topic [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span></span>  
  
 <span data-ttu-id="5d14e-111">Aby zachować odstępów w obrębie obiektu elementu zawartości, określ `xml:space="preserve"` w tym elemencie obiektu.</span><span class="sxs-lookup"><span data-stu-id="5d14e-111">To preserve whitespace within object element content, specify `xml:space="preserve"` on that object element.</span></span>  
  
 <span data-ttu-id="5d14e-112">W większości interpretacje `xml:space` efekty atrybutu, a wartość atrybutu ograniczone do elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="5d14e-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>  
  
 <span data-ttu-id="5d14e-113">Aby uzyskać szczegółowe omówienie przetwarzanie spacji w XAML, zobacz [przetwarzanie spacji w XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="5d14e-113">For a complete discussion of whitespace processing in XAML, see [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d14e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d14e-114">See Also</span></span>  
 [<span data-ttu-id="5d14e-115">Przetwarzanie spacji w XAML</span><span class="sxs-lookup"><span data-stu-id="5d14e-115">Whitespace Processing in XAML</span></span>](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)  
 [<span data-ttu-id="5d14e-116">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="5d14e-116">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
