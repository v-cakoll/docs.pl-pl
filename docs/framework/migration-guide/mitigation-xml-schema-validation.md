---
title: 'Środki zaradcze: Sprawdzanie poprawności schematu XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5c0087412a53177a7c43df838266f6d896c1bd9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220477"
---
# <a name="mitigation-xml-schema-validation"></a>Środki zaradcze: Sprawdzanie poprawności schematu XML
W [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], sprawdzanie poprawności schematu XSD wykryje naruszenie ograniczenia unique, jeśli jest używany klucz złożony i jeden klucz jest pusty.  
  
## <a name="impact"></a>Wpływ  
 Wpływ tej zmiany powinny być minimalne: oparte na specyfikacji schematu, błąd walidacji schematu oczekuje się, jeśli `xsd:unique` zostanie naruszona za pomocą klucza złożonego z pustym kluczem.  
  
## <a name="mitigation"></a>Ograniczenie  
 Czy wykrył błąd walidacji schematu, jeśli klucza złożonego ma jeden z pustym kluczem jest funkcją można skonfigurować:  
  
-   Począwszy od aplikacji, których platformą docelową [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], wykrywanie błąd walidacji schematu jest domyślnie włączona; jednak istnieje możliwość zrezygnować z niego tak, aby nie zostanie wykryty błąd walidacji schematu.  
  
-   W aplikacjach uruchamianych w ramach [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] , ale docelowa [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] i wcześniejszych wersjach, błąd walidacji schematu nie zostanie wykryty domyślnie; jednak istnieje możliwość zoptymalizowany pod kątem do niego, dzięki czemu zostanie wykryty błąd walidacji schematu.  
  
 To zachowanie można skonfigurować za pomocą <xref:System.AppContext> klasy do definiowania wartości `System.Xml.IgnoreEmptyKeySequences` przełącznika. Ponieważ przełącznik na wartość domyślna to `false` (pusty sekwencji klawiszy nie są ignorowane), aplikacje, których platformą docelową [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] można zrezygnować z zachowaniem przy użyciu następującego kodu, aby ustawić wartość przełącznika `true`:  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 W przypadku aplikacji, których platformą docelową [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] i wcześniejszymi wersjami, ponieważ przełącznik na wartość domyślna to `true` (pusty sekwencji klawiszy są ignorowane), istnieje możliwość upewnić się, że klucza złożonego z pustym kluczem wygenerować błąd walidacji schematu za pomocą następujący kod, aby ustawić wartość przełącznika `false`.  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
