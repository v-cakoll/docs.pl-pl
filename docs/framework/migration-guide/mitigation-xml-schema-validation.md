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
# <a name="mitigation-xml-schema-validation"></a>Ograniczenie: weryfikacja schematu XML
W .NET Framework 4.6 sprawdzanie poprawności schematu XSD wykrywa naruszenie ograniczenia unikatowego, jeśli klucz złożony jest używany i jeden klucz jest pusty.  
  
## <a name="impact"></a>Wpływ  
 Wpływ tej zmiany powinien być minimalny: na podstawie specyfikacji schematu oczekiwany jest błąd sprawdzania poprawności schematu, jeśli `xsd:unique` zostanie naruszony przy użyciu klucza złożonego z pustym kluczem.  
  
## <a name="mitigation"></a>Środki zaradcze  
 Czy błąd sprawdzania poprawności schematu jest wykrywany, jeśli klucz złożony ma jeden pusty klucz jest konfigurowalną funkcją:  
  
- Począwszy od aplikacji docelowych .NET Framework 4.6, wykrywanie błędu sprawdzania poprawności schematu jest domyślnie włączone; jednak istnieje możliwość zrezygnować z niego, tak aby błąd sprawdzania poprawności schematu nie zostaną wykryte.  
  
- W aplikacjach, które działają w ramach programu .NET Framework 4.6, ale są przeznaczone dla programu .NET Framework 4.5.2 i wcześniejszych wersji, błąd sprawdzania poprawności schematu nie jest domyślnie wykrywany; jednak jest możliwe, aby zdecydować się na to, tak aby zostanie wykryty błąd sprawdzania poprawności schematu.  
  
 To zachowanie można skonfigurować <xref:System.AppContext> za pomocą klasy do `System.Xml.IgnoreEmptyKeySequences` definiowania wartości przełącznika. Ponieważ domyślna wartość przełącznika jest `false` (puste sekwencje klawiszy nie są ignorowane), aplikacje przeznaczone dla programu .NET Framework 4.6 `true`mogą zrezygnować z zachowania, używając następującego kodu, aby ustawić wartość przełącznika na:  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 W przypadku aplikacji przeznaczonych dla platformy .NET Framework 4.5.2 i `true` wcześniejszych wersji, ponieważ domyślną wartością przełącznika jest (puste sekwencje klawiszy są ignorowane), można upewnić się, `false`że klucz złożony z pustym kluczem generuje błąd sprawdzania poprawności schematu przy użyciu następującego kodu, aby ustawić wartość przełącznika na .  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- [Zgodność aplikacji](application-compatibility.md)
