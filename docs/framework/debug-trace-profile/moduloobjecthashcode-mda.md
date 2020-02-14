---
title: moduloObjectHashcode MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), hashcode modulus
- Modulo object hash code
- moduloObjectHashcode MDA
- hashcode modulus
- MDAs (managed debugging assistants), hashcode modulus
- GetHashCode method
- modulus of hashcodes
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
ms.openlocfilehash: 65bbdfec2d7050d1b474a8186a9ea6e9bb93bd9e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216182"
---
# <a name="moduloobjecthashcode-mda"></a>moduloObjectHashcode MDA
`moduloObjectHashcode` zarządzanego asystenta debugowania (MDA) zmienia zachowanie klasy <xref:System.Object>, aby wykonać operację modulo dla kodu skrótu zwracanego przez metodę <xref:System.Object.GetHashCode%2A>. Domyślny moduł dla tego elementu MDA wynosi 1, co powoduje, że <xref:System.Object.GetHashCode%2A> zwrócić wartość 0 dla wszystkich obiektów.  
  
## <a name="symptoms"></a>Objawy  
 Po przejściu do nowej wersji środowiska uruchomieniowego języka wspólnego (CLR) program nie jest już wykonywany prawidłowo:  
  
- Program pobiera nieprawidłowy obiekt z <xref:System.Collections.Hashtable>.  
  
- Kolejność wyliczania na podstawie <xref:System.Collections.Hashtable> ma zmianę, która powoduje przerwanie działania programu.  
  
- Dwa obiekty, które były takie same, nie są już równe.  
  
- Dwa obiekty, które nie są równe, są teraz równe.  
  
## <a name="cause"></a>Przyczyna  
 Program może uzyskać niewłaściwy obiekt z <xref:System.Collections.Hashtable>, ponieważ implementacja metody <xref:System.Object.Equals%2A> na klasie dla klucza w <xref:System.Collections.Hashtable> testy pod kątem równości obiektów, porównując wyniki wywołania metody <xref:System.Object.GetHashCode%2A>. Kodów skrótów nie należy używać do testowania równości obiektów, ponieważ dwa obiekty mogą mieć ten sam kod skrótu, nawet jeśli odpowiadające im pola mają różne wartości. Te konflikty kodu mieszania, chociaż rzadko występują, są wykonywane. Efekt na wyszukiwaniu <xref:System.Collections.Hashtable> polega na tym, że dwa klucze, które nie są równe, są równe, i zwracany jest nieprawidłowy obiekt z <xref:System.Collections.Hashtable>. Ze względu na wydajność implementacja <xref:System.Object.GetHashCode%2A> może ulec zmianie między wersjami środowiska uruchomieniowego, więc kolizje, które mogą nie wystąpić w jednej wersji, mogą wystąpić w kolejnych wersjach. Włącz tę funkcję MDA, aby sprawdzić, czy kod ma błędy w przypadku kolizji kodów mieszania. Gdy ta funkcja jest włączona, to zdarzenie MDA spowoduje zwrócenie wartości 0 przez metodę <xref:System.Object.GetHashCode%2A>, co spowodowało kolizję wszystkich kodów skrótu. Jedynym efektem włączenia tego pakietu w programie jest to, że program działa wolniej.  
  
 Kolejność wyliczania z <xref:System.Collections.Hashtable> może ulec zmianie z jednej wersji środowiska uruchomieniowego na inną, jeśli algorytm używany do obliczania kodów skrótów dla zmiany klucza. Aby sprawdzić, czy program pobrał zależność od kolejności wyliczania kluczy lub wartości z tabeli skrótów, można włączyć to zdarzenie MDA.  
  
## <a name="resolution"></a>Rozwiązanie  
 Nigdy nie używaj kodów skrótu jako substytutu dla tożsamości obiektu. Zaimplementuj przesłonięcie metody <xref:System.Object.Equals%2A?displayProperty=nameWithType>, aby nie porównywać kodów skrótów.  
  
 Nie należy tworzyć zależności względem kolejności wyliczeń kluczy lub wartości w tabelach skrótów.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Aplikacje działają wolniej, gdy to MDA jest włączone. To zdarzenie MDA po prostu pobiera zwrócony kod skrótu, a zamiast tego zwraca resztę przy poddzieleniu przez moduł.  
  
## <a name="output"></a>Dane wyjściowe  
 Brak danych wyjściowych dla tego MDA.  
  
## <a name="configuration"></a>Konfiguracja  
 Atrybut `modulus` określa moduł używany w kodzie skrótu. Wartość domyślna to 1.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
