---
title: xml:space — Obsługa w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 8f860f5ee42b5c1df43c4ec2b1003408bc1c0d8e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458793"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="58b04-102">xml:space — Obsługa w XAML</span><span class="sxs-lookup"><span data-stu-id="58b04-102">xml:space Handling in XAML</span></span>
<span data-ttu-id="58b04-103">Atrybut `xml:space` jest atrybutem zdefiniowanym przez XML, który deklaruje znaczące zachowanie przetwarzania białych miejsc wewnątrz elementu obiektu.</span><span class="sxs-lookup"><span data-stu-id="58b04-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="58b04-104">To zachowanie dotyczy całej zawartości (tekst wewnętrzny) zawartej w elemencie, gdzie `xml:space` jest zadeklarowana, a także zakresy do elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="58b04-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="58b04-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="58b04-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 <span data-ttu-id="58b04-106">\- lub-</span><span class="sxs-lookup"><span data-stu-id="58b04-106">\- or -</span></span>  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a><span data-ttu-id="58b04-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58b04-107">Remarks</span></span>  
 <span data-ttu-id="58b04-108">Definicja atrybutu `xml:space` w języku XAML, w tym jej dwie możliwe wartości, pochodzi od `xml:space`, jak zdefiniowano jako "atrybut specjalny" przez specyfikacje W3C dla XML.</span><span class="sxs-lookup"><span data-stu-id="58b04-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>  
  
 <span data-ttu-id="58b04-109">Wartość domyślna atrybutu `xml:space` jest wartością literału `"default"`.</span><span class="sxs-lookup"><span data-stu-id="58b04-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="58b04-110">Dla wartości `"default"`, lub jeśli w ogóle nie określono `xml:space`, zachowanie znaczącej analizy białych znaków jest domyślną obsługą, zgodnie z definicją w temacie [Przetwarzanie bieli miejsca w języku XAML](whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="58b04-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
 <span data-ttu-id="58b04-111">Aby zachować biały znak w zawartości elementu obiektu, należy określić `xml:space="preserve"` w tym elemencie obiektu.</span><span class="sxs-lookup"><span data-stu-id="58b04-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>  
  
 <span data-ttu-id="58b04-112">W ramach większości interpretacji, `xml:space` efekty atrybutu i wartość atrybutu są zakresem elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="58b04-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>  
  
 <span data-ttu-id="58b04-113">Aby uzyskać pełną dyskusję na temat przetwarzania białych miejsc w języku XAML, zobacz artykuł [Przetwarzanie białych miejsc w języku XAML](whitespace-processing-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="58b04-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58b04-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58b04-114">See also</span></span>

- [<span data-ttu-id="58b04-115">Przetwarzanie białych miejsc w języku XAML</span><span class="sxs-lookup"><span data-stu-id="58b04-115">White-space processing in XAML</span></span>](whitespace-processing-in-xaml.md)
- [<span data-ttu-id="58b04-116">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="58b04-116">XAML Overview (WPF)</span></span>](../../desktop-wpf/fundamentals/xaml.md)
