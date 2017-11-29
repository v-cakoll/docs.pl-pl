---
title: 'Ograniczenie: walidacja schematu XML'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8bc8aab23490b5531a155798520936cacbd6a6d3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="65e74-102">Ograniczenie: walidacja schematu XML</span><span class="sxs-lookup"><span data-stu-id="65e74-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="65e74-103">W [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], Weryfikacja schematu XSD wykrywa naruszenie ograniczenia unique, jeśli jest używany klucz złożony i jeden klucz jest pusty.</span><span class="sxs-lookup"><span data-stu-id="65e74-103">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="65e74-104">Wpływ</span><span class="sxs-lookup"><span data-stu-id="65e74-104">Impact</span></span>  
 <span data-ttu-id="65e74-105">Wpływ tej zmiany należy minimalnego: oparte na specyfikacji schematu, błąd sprawdzania poprawności schematu upewnij się, czy `xsd:unique` naruszenia przy użyciu klucza złożonego z pustym kluczem.</span><span class="sxs-lookup"><span data-stu-id="65e74-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="65e74-106">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="65e74-106">Mitigation</span></span>  
 <span data-ttu-id="65e74-107">Określa, czy wykrył błąd sprawdzania poprawności schematu, jeśli klucza złożonego ma pusty klucz w jednym jest funkcją można skonfigurować:</span><span class="sxs-lookup"><span data-stu-id="65e74-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
-   <span data-ttu-id="65e74-108">Począwszy od aplikacji przeznaczonych [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], wykrywania błąd sprawdzania poprawności schematu jest domyślnie włączona; jednak jest możliwe rezygnacji z, tak aby nie zostanie wykryty błąd sprawdzania poprawności schematu.</span><span class="sxs-lookup"><span data-stu-id="65e74-108">Starting with the apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
-   <span data-ttu-id="65e74-109">W aplikacjach, które są uruchamiane w obszarze [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] , ale docelowy [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] i starszych wersjach, domyślnie nie zostanie wykryty błąd sprawdzania poprawności schematu; jednak istnieje możliwość opcjonalnych, dzięki czemu zostanie wykryty błąd sprawdzania poprawności schematu.</span><span class="sxs-lookup"><span data-stu-id="65e74-109">In apps that run under the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] but target the [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="65e74-110">To zachowanie można skonfigurować przy użyciu <xref:System.AppContext> klasę, aby zdefiniować wartość `System.Xml.IgnoreEmptyKeySequences` przełącznika.</span><span class="sxs-lookup"><span data-stu-id="65e74-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="65e74-111">Ponieważ przełącznika wartość domyślna to `false` (puste sekwencje klucza nie są ignorowane), aplikacje, które odnoszą się do [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] można zrezygnować z zachowanie, używając następującego kodu ustawioną wartość przełącznika `true`:</span><span class="sxs-lookup"><span data-stu-id="65e74-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="65e74-112">Dla aplikacji, które odnoszą się do [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] i starszych wersjach, ponieważ przełącznik wartość domyślna to `true` (puste sekwencje klucza są ignorowane), istnieje możliwość upewnić się, że klucza złożonego z pustym kluczem wygenerować błąd sprawdzania poprawności schematu za pomocą następującego kodu, aby ustawić wartość przełącznika `false`.</span><span class="sxs-lookup"><span data-stu-id="65e74-112">For apps that target the [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="65e74-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65e74-113">See Also</span></span>  
 [<span data-ttu-id="65e74-114">Zmiany retargetingu</span><span class="sxs-lookup"><span data-stu-id="65e74-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
