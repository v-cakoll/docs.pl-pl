---
title: Środki zaradcze Walidacja schematu XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7f53a2e8684029c0d1329d29a88bd1788e62d43
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789681"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="8c36f-102">Środki zaradcze Walidacja schematu XML</span><span class="sxs-lookup"><span data-stu-id="8c36f-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="8c36f-103">W .NET Framework 4,6 Walidacja schematu XSD wykrywa naruszenie ograniczenia UNIQUE w przypadku użycia klucza złożonego, a jeden klucz jest pusty.</span><span class="sxs-lookup"><span data-stu-id="8c36f-103">In the .NET Framework 4.6, XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="8c36f-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="8c36f-104">Impact</span></span>  
 <span data-ttu-id="8c36f-105">Wpływ tej zmiany powinien być minimalny: na podstawie specyfikacji schematu, oczekiwany jest błąd walidacji schematu, jeśli `xsd:unique` jest on naruszany przy użyciu klucza złożonego z pustym kluczem.</span><span class="sxs-lookup"><span data-stu-id="8c36f-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="8c36f-106">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="8c36f-106">Mitigation</span></span>  
 <span data-ttu-id="8c36f-107">Czy wykryto błąd sprawdzania poprawności schematu, jeśli klucz złożony ma jeden pusty klucz, który jest konfigurowalną funkcją:</span><span class="sxs-lookup"><span data-stu-id="8c36f-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
- <span data-ttu-id="8c36f-108">Począwszy od aplikacji przeznaczonych dla .NET Framework 4,6, wykrywanie błędu walidacji schematu jest domyślnie włączone; można jednak zrezygnować z niego, aby błąd sprawdzania poprawności schematu nie zostanie wykryty.</span><span class="sxs-lookup"><span data-stu-id="8c36f-108">Starting with the apps that target the .NET Framework 4.6, detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
- <span data-ttu-id="8c36f-109">W aplikacjach uruchamianych w .NET Framework 4,6, ale przeznaczonych dla .NET Framework 4.5.2 i starszych wersji, błąd walidacji schematu nie jest domyślnie wykrywany; możliwe jest jednak, aby to umożliwić, aby wykrycie błędu walidacji schematu.</span><span class="sxs-lookup"><span data-stu-id="8c36f-109">In apps that run under the .NET Framework 4.6 but target the .NET Framework 4.5.2 and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="8c36f-110">Takie zachowanie można skonfigurować przy użyciu <xref:System.AppContext> klasy do definiowania wartości `System.Xml.IgnoreEmptyKeySequences` przełącznika.</span><span class="sxs-lookup"><span data-stu-id="8c36f-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="8c36f-111">Ponieważ domyślna wartość przełącznika to `false` (puste sekwencje klawiszy nie są ignorowane), aplikacje przeznaczone dla .NET Framework 4,6 mogą zrezygnować z zachowania przy użyciu następującego kodu, aby ustawić wartość przełącznika na: `true`</span><span class="sxs-lookup"><span data-stu-id="8c36f-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the .NET Framework 4.6 can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="8c36f-112">W przypadku aplikacji, które są przeznaczone dla .NET Framework 4.5.2 i starszych wersji, ponieważ domyślna wartość przełącznika `true` to (puste sekwencje klawiszy są ignorowane), istnieje możliwość upewnienia się, że klucz złożony z pustym kluczem generuje błąd walidacji schematu przy użyciu Poniższy kod, aby ustawić wartość `false`przełącznika.</span><span class="sxs-lookup"><span data-stu-id="8c36f-112">For apps that target the .NET Framework 4.5.2 and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8c36f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c36f-113">See also</span></span>

- [<span data-ttu-id="8c36f-114">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="8c36f-114">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
