---
title: 'Ograniczenie: weryfikacja schematu XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
ms.openlocfilehash: 7feed7de4a6c76f5f2ba0e2ea1c532aad6bde4de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126070"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="3ea2d-102">Ograniczenie: weryfikacja schematu XML</span><span class="sxs-lookup"><span data-stu-id="3ea2d-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="3ea2d-103">W .NET Framework 4,6 Walidacja schematu XSD wykrywa naruszenie ograniczenia UNIQUE w przypadku użycia klucza złożonego, a jeden klucz jest pusty.</span><span class="sxs-lookup"><span data-stu-id="3ea2d-103">In the .NET Framework 4.6, XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="3ea2d-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="3ea2d-104">Impact</span></span>  
 <span data-ttu-id="3ea2d-105">Wpływ tej zmiany powinien być minimalny: na podstawie specyfikacji schematu, oczekiwany jest błąd sprawdzania poprawności schematu w przypadku naruszenia `xsd:unique` przy użyciu klucza złożonego z pustym kluczem.</span><span class="sxs-lookup"><span data-stu-id="3ea2d-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="3ea2d-106">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="3ea2d-106">Mitigation</span></span>  
 <span data-ttu-id="3ea2d-107">Czy wykryto błąd sprawdzania poprawności schematu, jeśli klucz złożony ma jeden pusty klucz, który jest konfigurowalną funkcją:</span><span class="sxs-lookup"><span data-stu-id="3ea2d-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
- <span data-ttu-id="3ea2d-108">Począwszy od aplikacji przeznaczonych dla .NET Framework 4,6, wykrywanie błędu walidacji schematu jest domyślnie włączone; można jednak zrezygnować z niego, aby błąd sprawdzania poprawności schematu nie zostanie wykryty.</span><span class="sxs-lookup"><span data-stu-id="3ea2d-108">Starting with the apps that target the .NET Framework 4.6, detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
- <span data-ttu-id="3ea2d-109">W aplikacjach uruchamianych w .NET Framework 4,6, ale przeznaczonych dla .NET Framework 4.5.2 i starszych wersji, błąd walidacji schematu nie jest domyślnie wykrywany; możliwe jest jednak, aby to umożliwić, aby wykrycie błędu walidacji schematu.</span><span class="sxs-lookup"><span data-stu-id="3ea2d-109">In apps that run under the .NET Framework 4.6 but target the .NET Framework 4.5.2 and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="3ea2d-110">Takie zachowanie można skonfigurować przy użyciu klasy <xref:System.AppContext> do definiowania wartości przełącznika `System.Xml.IgnoreEmptyKeySequences`.</span><span class="sxs-lookup"><span data-stu-id="3ea2d-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="3ea2d-111">Ponieważ domyślna wartość przełącznika to `false` (puste sekwencje klawiszy nie są ignorowane), aplikacje przeznaczone dla .NET Framework 4,6 mogą zrezygnować z zachowania przy użyciu następującego kodu, aby ustawić wartość przełącznika na `true`:</span><span class="sxs-lookup"><span data-stu-id="3ea2d-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the .NET Framework 4.6 can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="3ea2d-112">W przypadku aplikacji, które są przeznaczone dla .NET Framework 4.5.2 i starszych wersji, ponieważ domyślna wartość przełącznika jest `true` (puste sekwencje klawiszy są ignorowane), istnieje możliwość zapewnienia, że klucz złożony z pustym kluczem generuje błąd walidacji schematu przy użyciu Poniższy kod umożliwia ustawienie wartości przełącznika na `false`.</span><span class="sxs-lookup"><span data-stu-id="3ea2d-112">For apps that target the .NET Framework 4.5.2 and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="3ea2d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ea2d-113">See also</span></span>

- [<span data-ttu-id="3ea2d-114">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="3ea2d-114">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
