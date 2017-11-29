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
# <a name="mitigation-xml-schema-validation"></a>Ograniczenie: walidacja schematu XML
W [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], Weryfikacja schematu XSD wykrywa naruszenie ograniczenia unique, jeśli jest używany klucz złożony i jeden klucz jest pusty.  
  
## <a name="impact"></a>Wpływ  
 Wpływ tej zmiany należy minimalnego: oparte na specyfikacji schematu, błąd sprawdzania poprawności schematu upewnij się, czy `xsd:unique` naruszenia przy użyciu klucza złożonego z pustym kluczem.  
  
## <a name="mitigation"></a>Ograniczenie  
 Określa, czy wykrył błąd sprawdzania poprawności schematu, jeśli klucza złożonego ma pusty klucz w jednym jest funkcją można skonfigurować:  
  
-   Począwszy od aplikacji przeznaczonych [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], wykrywania błąd sprawdzania poprawności schematu jest domyślnie włączona; jednak jest możliwe rezygnacji z, tak aby nie zostanie wykryty błąd sprawdzania poprawności schematu.  
  
-   W aplikacjach, które są uruchamiane w obszarze [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] , ale docelowy [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] i starszych wersjach, domyślnie nie zostanie wykryty błąd sprawdzania poprawności schematu; jednak istnieje możliwość opcjonalnych, dzięki czemu zostanie wykryty błąd sprawdzania poprawności schematu.  
  
 To zachowanie można skonfigurować przy użyciu <xref:System.AppContext> klasę, aby zdefiniować wartość `System.Xml.IgnoreEmptyKeySequences` przełącznika. Ponieważ przełącznika wartość domyślna to `false` (puste sekwencje klucza nie są ignorowane), aplikacje, które odnoszą się do [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] można zrezygnować z zachowanie, używając następującego kodu ustawioną wartość przełącznika `true`:  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 Dla aplikacji, które odnoszą się do [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] i starszych wersjach, ponieważ przełącznik wartość domyślna to `true` (puste sekwencje klucza są ignorowane), istnieje możliwość upewnić się, że klucza złożonego z pustym kluczem wygenerować błąd sprawdzania poprawności schematu za pomocą następującego kodu, aby ustawić wartość przełącznika `false`.  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
