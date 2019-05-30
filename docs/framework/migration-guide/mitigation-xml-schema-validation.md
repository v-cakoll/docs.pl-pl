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
# <a name="mitigation-xml-schema-validation"></a>Środki zaradcze: Sprawdzanie poprawności schematu XML
W .NET Framework 4.6 Weryfikacja schematu XSD wykrywa naruszenie ograniczenia unique, jeśli jest używany klucz złożony i jeden klucz jest pusty.  
  
## <a name="impact"></a>Wpływ  
 Wpływ tej zmiany powinny być minimalne: oparte na specyfikacji schematu, błąd walidacji schematu oczekuje się, jeśli `xsd:unique` zostanie naruszona za pomocą klucza złożonego z pustym kluczem.  
  
## <a name="mitigation"></a>Ograniczenie  
 Czy wykrył błąd walidacji schematu, jeśli klucza złożonego ma jeden z pustym kluczem jest funkcją można skonfigurować:  
  
- Począwszy od aplikacji przeznaczonych na .NET Framework 4.6, wykrywanie błąd walidacji schematu jest domyślnie włączona; jednak użytkownik może zrezygnować z niego tak, aby nie zostanie wykryty błąd walidacji schematu.  
  
- W aplikacjach, które działania programu .NET Framework 4.6, ale docelowej platformy .NET Framework 4.5.2 i wcześniejszych wersjach błąd walidacji schematu nie zostanie wykryty domyślnie; jednak istnieje możliwość zoptymalizowany pod kątem do niego, dzięki czemu zostanie wykryty błąd walidacji schematu.  
  
 To zachowanie można skonfigurować za pomocą <xref:System.AppContext> klasy do definiowania wartości `System.Xml.IgnoreEmptyKeySequences` przełącznika. Ponieważ przełącznik na wartość domyślna to `false` (pusty sekwencji klawiszy nie są ignorowane), aplikacji przeznaczonych dla platformy .NET Framework 4.6 można zrezygnować z zachowanie, używając następującego kodu, aby ustawić wartość przełącznika `true`:  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 W przypadku aplikacji, których platformą docelową .NET Framework 4.5.2 i wcześniejszymi wersjami, ponieważ przełącznik na wartość domyślna to `true` (pusty sekwencji klawiszy są ignorowane), istnieje możliwość upewnić się, że klucza złożonego z pustym kluczem wygenerować błąd walidacji schematu za pomocą Poniższy kod, aby ustawić wartość przełącznika `false`.  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Zmiany retargetingu](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
