---
title: 'Środki zaradcze: Sprawdzanie poprawności schematu XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36f9475a978ddf7253833e6c3372049d24502f95
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300581"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="369bb-102">Środki zaradcze: Sprawdzanie poprawności schematu XML</span><span class="sxs-lookup"><span data-stu-id="369bb-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="369bb-103">W .NET Framework 4.6 Weryfikacja schematu XSD wykrywa naruszenie ograniczenia unique, jeśli jest używany klucz złożony i jeden klucz jest pusty.</span><span class="sxs-lookup"><span data-stu-id="369bb-103">In the .NET Framework 4.6, XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="369bb-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="369bb-104">Impact</span></span>  
 <span data-ttu-id="369bb-105">Wpływ tej zmiany powinny być minimalne: oparte na specyfikacji schematu, błąd walidacji schematu oczekuje się, jeśli `xsd:unique` zostanie naruszona za pomocą klucza złożonego z pustym kluczem.</span><span class="sxs-lookup"><span data-stu-id="369bb-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="369bb-106">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="369bb-106">Mitigation</span></span>  
 <span data-ttu-id="369bb-107">Czy wykrył błąd walidacji schematu, jeśli klucza złożonego ma jeden z pustym kluczem jest funkcją można skonfigurować:</span><span class="sxs-lookup"><span data-stu-id="369bb-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
- <span data-ttu-id="369bb-108">Począwszy od aplikacji przeznaczonych na .NET Framework 4.6, wykrywanie błąd walidacji schematu jest domyślnie włączona; jednak użytkownik może zrezygnować z niego tak, aby nie zostanie wykryty błąd walidacji schematu.</span><span class="sxs-lookup"><span data-stu-id="369bb-108">Starting with the apps that target the .NET Framework 4.6, detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
- <span data-ttu-id="369bb-109">W aplikacjach, które działania programu .NET Framework 4.6, ale docelowej platformy .NET Framework 4.5.2 i wcześniejszych wersjach błąd walidacji schematu nie zostanie wykryty domyślnie; jednak istnieje możliwość zoptymalizowany pod kątem do niego, dzięki czemu zostanie wykryty błąd walidacji schematu.</span><span class="sxs-lookup"><span data-stu-id="369bb-109">In apps that run under the .NET Framework 4.6 but target the .NET Framework 4.5.2 and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="369bb-110">To zachowanie można skonfigurować za pomocą <xref:System.AppContext> klasy do definiowania wartości `System.Xml.IgnoreEmptyKeySequences` przełącznika.</span><span class="sxs-lookup"><span data-stu-id="369bb-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="369bb-111">Ponieważ przełącznik na wartość domyślna to `false` (pusty sekwencji klawiszy nie są ignorowane), aplikacji przeznaczonych dla platformy .NET Framework 4.6 można zrezygnować z zachowanie, używając następującego kodu, aby ustawić wartość przełącznika `true`:</span><span class="sxs-lookup"><span data-stu-id="369bb-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the .NET Framework 4.6 can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="369bb-112">W przypadku aplikacji, których platformą docelową .NET Framework 4.5.2 i wcześniejszymi wersjami, ponieważ przełącznik na wartość domyślna to `true` (pusty sekwencji klawiszy są ignorowane), istnieje możliwość upewnić się, że klucza złożonego z pustym kluczem wygenerować błąd walidacji schematu za pomocą Poniższy kod, aby ustawić wartość przełącznika `false`.</span><span class="sxs-lookup"><span data-stu-id="369bb-112">For apps that target the .NET Framework 4.5.2 and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="369bb-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="369bb-113">See also</span></span>

- [<span data-ttu-id="369bb-114">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="369bb-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
