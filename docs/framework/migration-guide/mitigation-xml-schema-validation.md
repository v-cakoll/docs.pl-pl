---
title: 'Ograniczenie: weryfikacja schematu XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
ms.openlocfilehash: 99cc1eae08697909d89e5c1e46cd604c7da543bc
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457738"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="fce64-102">Ograniczenie: weryfikacja schematu XML</span><span class="sxs-lookup"><span data-stu-id="fce64-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="fce64-103">W .NET Framework 4,6 Walidacja schematu XSD wykrywa naruszenie ograniczenia UNIQUE w przypadku użycia klucza złożonego, a jeden klucz jest pusty.</span><span class="sxs-lookup"><span data-stu-id="fce64-103">In the .NET Framework 4.6, XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="fce64-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="fce64-104">Impact</span></span>  
 <span data-ttu-id="fce64-105">Wpływ tej zmiany powinien być minimalny: na podstawie specyfikacji schematu, oczekiwany jest błąd sprawdzania poprawności schematu w przypadku naruszenia `xsd:unique` przy użyciu klucza złożonego z pustym kluczem.</span><span class="sxs-lookup"><span data-stu-id="fce64-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="fce64-106">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="fce64-106">Mitigation</span></span>  
 <span data-ttu-id="fce64-107">Czy wykryto błąd sprawdzania poprawności schematu, jeśli klucz złożony ma jeden pusty klucz, który jest konfigurowalną funkcją:</span><span class="sxs-lookup"><span data-stu-id="fce64-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
- <span data-ttu-id="fce64-108">Począwszy od aplikacji przeznaczonych dla .NET Framework 4,6, wykrywanie błędu walidacji schematu jest domyślnie włączone; można jednak zrezygnować z niego, aby błąd sprawdzania poprawności schematu nie zostanie wykryty.</span><span class="sxs-lookup"><span data-stu-id="fce64-108">Starting with the apps that target the .NET Framework 4.6, detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
- <span data-ttu-id="fce64-109">W aplikacjach uruchamianych w .NET Framework 4,6, ale przeznaczonych dla .NET Framework 4.5.2 i starszych wersji, błąd walidacji schematu nie jest domyślnie wykrywany; możliwe jest jednak, aby to umożliwić, aby wykrycie błędu walidacji schematu.</span><span class="sxs-lookup"><span data-stu-id="fce64-109">In apps that run under the .NET Framework 4.6 but target the .NET Framework 4.5.2 and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="fce64-110">Takie zachowanie można skonfigurować przy użyciu klasy <xref:System.AppContext> do definiowania wartości przełącznika `System.Xml.IgnoreEmptyKeySequences`.</span><span class="sxs-lookup"><span data-stu-id="fce64-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="fce64-111">Ponieważ domyślna wartość przełącznika to `false` (puste sekwencje klawiszy nie są ignorowane), aplikacje przeznaczone dla .NET Framework 4,6 mogą zrezygnować z zachowania przy użyciu następującego kodu, aby ustawić wartość przełącznika na `true`:</span><span class="sxs-lookup"><span data-stu-id="fce64-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the .NET Framework 4.6 can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="fce64-112">W przypadku aplikacji, które są przeznaczone dla .NET Framework 4.5.2 i starszych wersji, ponieważ domyślna wartość przełącznika jest `true` (puste sekwencje klawiszy są ignorowane), istnieje możliwość zapewnienia, że klucz złożony z pustym kluczem generuje błąd walidacji schematu przy użyciu Poniższy kod umożliwia ustawienie wartości przełącznika na `false`.</span><span class="sxs-lookup"><span data-stu-id="fce64-112">For apps that target the .NET Framework 4.5.2 and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="fce64-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fce64-113">See also</span></span>

- [<span data-ttu-id="fce64-114">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="fce64-114">Application compatibility</span></span>](application-compatibility.md)
