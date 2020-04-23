---
title: xml:space — Obsługa w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 886f906b6d1e3a10920dbf52e36bf76324c5a9f2
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071438"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="7d0dc-102">xml:space — Obsługa w XAML</span><span class="sxs-lookup"><span data-stu-id="7d0dc-102">xml:space Handling in XAML</span></span>

<span data-ttu-id="7d0dc-103">Atrybut `xml:space` jest atrybutem zdefiniowanym przez XML, który deklaruje znaczące zachowanie przetwarzania odstępu w elemencie obiektu.</span><span class="sxs-lookup"><span data-stu-id="7d0dc-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="7d0dc-104">To zachowanie jest istotne dla całej zawartości (tekst `xml:space` wewnętrzny) zawarte w elemencie, gdzie jest zadeklarowany, a także zakresy do elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="7d0dc-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="7d0dc-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="7d0dc-105">XAML Attribute Usage</span></span>

```xaml
<object xml:space="preserve" />
```

 <span data-ttu-id="7d0dc-106">\-lub -</span><span class="sxs-lookup"><span data-stu-id="7d0dc-106">\- or -</span></span>

```xaml
<object xml:space="default" />
```

## <a name="remarks"></a><span data-ttu-id="7d0dc-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d0dc-107">Remarks</span></span>

<span data-ttu-id="7d0dc-108">Definicja atrybutu `xml:space` w języku XAML, w tym `xml:space` jego dwie możliwe wartości, jest wyprowadzana jako zdefiniowana jako "atrybut specjalny" według specyfikacji W3C dla XML.</span><span class="sxs-lookup"><span data-stu-id="7d0dc-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>

<span data-ttu-id="7d0dc-109">Domyślną wartością `xml:space` atrybutu jest wartość `"default"`literału .</span><span class="sxs-lookup"><span data-stu-id="7d0dc-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="7d0dc-110">Dla wartości `"default"`, `xml:space` lub jeśli nie jest wskazany w ogóle, zachowanie znaczących analizowania odstępu jest domyślną obsługą, zgodnie z definicją w temacie [Przetwarzanie odstępu w XAML](white-space-processing.md).</span><span class="sxs-lookup"><span data-stu-id="7d0dc-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](white-space-processing.md).</span></span>

<span data-ttu-id="7d0dc-111">Aby zachować odstępy w `xml:space="preserve"` zawartości elementu obiektu, należy określić w tym elemencie obiektu.</span><span class="sxs-lookup"><span data-stu-id="7d0dc-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>

<span data-ttu-id="7d0dc-112">W większości interpretacji `xml:space` efekty atrybutu i wartość atrybutu są ograniczone do elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="7d0dc-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>

<span data-ttu-id="7d0dc-113">Aby uzyskać pełną dyskusję na temat przetwarzania odstępów w języku XAML, zobacz [Przetwarzanie odstępów w języku XAML](white-space-processing.md).</span><span class="sxs-lookup"><span data-stu-id="7d0dc-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](white-space-processing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7d0dc-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d0dc-114">See also</span></span>

- [<span data-ttu-id="7d0dc-115">Przetwarzanie spacji w XAML</span><span class="sxs-lookup"><span data-stu-id="7d0dc-115">White-space processing in XAML</span></span>](white-space-processing.md)
- [<span data-ttu-id="7d0dc-116">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="7d0dc-116">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
