---
title: 'Ograniczenie: weryfikacja schematu XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
ms.openlocfilehash: 99cc1eae08697909d89e5c1e46cd604c7da543bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457738"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="eb9e6-102">Ograniczenie: weryfikacja schematu XML</span><span class="sxs-lookup"><span data-stu-id="eb9e6-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="eb9e6-103">W .NET Framework 4.6 sprawdzanie poprawności schematu XSD wykrywa naruszenie ograniczenia unikatowego, jeśli klucz złożony jest używany i jeden klucz jest pusty.</span><span class="sxs-lookup"><span data-stu-id="eb9e6-103">In the .NET Framework 4.6, XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="eb9e6-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="eb9e6-104">Impact</span></span>  
 <span data-ttu-id="eb9e6-105">Wpływ tej zmiany powinien być minimalny: na podstawie specyfikacji schematu oczekiwany jest błąd sprawdzania poprawności schematu, jeśli `xsd:unique` zostanie naruszony przy użyciu klucza złożonego z pustym kluczem.</span><span class="sxs-lookup"><span data-stu-id="eb9e6-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="eb9e6-106">Środki zaradcze</span><span class="sxs-lookup"><span data-stu-id="eb9e6-106">Mitigation</span></span>  
 <span data-ttu-id="eb9e6-107">Czy błąd sprawdzania poprawności schematu jest wykrywany, jeśli klucz złożony ma jeden pusty klucz jest konfigurowalną funkcją:</span><span class="sxs-lookup"><span data-stu-id="eb9e6-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
- <span data-ttu-id="eb9e6-108">Począwszy od aplikacji docelowych .NET Framework 4.6, wykrywanie błędu sprawdzania poprawności schematu jest domyślnie włączone; jednak istnieje możliwość zrezygnować z niego, tak aby błąd sprawdzania poprawności schematu nie zostaną wykryte.</span><span class="sxs-lookup"><span data-stu-id="eb9e6-108">Starting with the apps that target the .NET Framework 4.6, detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
- <span data-ttu-id="eb9e6-109">W aplikacjach, które działają w ramach programu .NET Framework 4.6, ale są przeznaczone dla programu .NET Framework 4.5.2 i wcześniejszych wersji, błąd sprawdzania poprawności schematu nie jest domyślnie wykrywany; jednak jest możliwe, aby zdecydować się na to, tak aby zostanie wykryty błąd sprawdzania poprawności schematu.</span><span class="sxs-lookup"><span data-stu-id="eb9e6-109">In apps that run under the .NET Framework 4.6 but target the .NET Framework 4.5.2 and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="eb9e6-110">To zachowanie można skonfigurować <xref:System.AppContext> za pomocą klasy do `System.Xml.IgnoreEmptyKeySequences` definiowania wartości przełącznika.</span><span class="sxs-lookup"><span data-stu-id="eb9e6-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="eb9e6-111">Ponieważ domyślna wartość przełącznika jest `false` (puste sekwencje klawiszy nie są ignorowane), aplikacje przeznaczone dla programu .NET Framework 4.6 `true`mogą zrezygnować z zachowania, używając następującego kodu, aby ustawić wartość przełącznika na:</span><span class="sxs-lookup"><span data-stu-id="eb9e6-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the .NET Framework 4.6 can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="eb9e6-112">W przypadku aplikacji przeznaczonych dla platformy .NET Framework 4.5.2 i `true` wcześniejszych wersji, ponieważ domyślną wartością przełącznika jest (puste sekwencje klawiszy są ignorowane), można upewnić się, `false`że klucz złożony z pustym kluczem generuje błąd sprawdzania poprawności schematu przy użyciu następującego kodu, aby ustawić wartość przełącznika na .</span><span class="sxs-lookup"><span data-stu-id="eb9e6-112">For apps that target the .NET Framework 4.5.2 and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="eb9e6-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb9e6-113">See also</span></span>

- [<span data-ttu-id="eb9e6-114">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="eb9e6-114">Application compatibility</span></span>](application-compatibility.md)
