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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1679e283a801044ad5a0baed89f17e6acc74259c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052459"
---
# <a name="moduloobjecthashcode-mda"></a>moduloObjectHashcode MDA
Asystent debugowania <xref:System.Object> <xref:System.Object.GetHashCode%2A> zarządzanego (MDA) zmienia zachowanie klasy w celu wykonania operacji modulo dla kodu skrótu zwracanego przez metodę. `moduloObjectHashcode` Domyślny moduł dla tego elementu MDA wynosi 1, co powoduje <xref:System.Object.GetHashCode%2A> zwrócenie wartości 0 dla wszystkich obiektów.  
  
## <a name="symptoms"></a>Symptomy  
 Po przejściu do nowej wersji środowiska uruchomieniowego języka wspólnego (CLR) program nie jest już wykonywany prawidłowo:  
  
- Program pobiera nieprawidłowy obiekt z <xref:System.Collections.Hashtable>.  
  
- Kolejność wyliczania z elementu a <xref:System.Collections.Hashtable> ma zmianę, która powoduje przerwanie działania programu.  
  
- Dwa obiekty, które były takie same, nie są już równe.  
  
- Dwa obiekty, które nie są równe, są teraz równe.  
  
## <a name="cause"></a>Przyczyna  
 Program <xref:System.Collections.Hashtable> może uzyskać niewłaściwy obiekt z, ponieważ implementacja <xref:System.Object.Equals%2A> metody klasy <xref:System.Collections.Hashtable> dla klucza w testach w celu równości obiektów przez <xref:System.Object.GetHashCode%2A> porównanie wyników wywołania metody. . Kodów skrótów nie należy używać do testowania równości obiektów, ponieważ dwa obiekty mogą mieć ten sam kod skrótu, nawet jeśli odpowiadające im pola mają różne wartości. Te konflikty kodu mieszania, chociaż rzadko występują, są wykonywane. Efekt na <xref:System.Collections.Hashtable> wyszukiwaniu polega na tym, że dwa klucze, które nie są równe, są równe, a niewłaściwy obiekt jest zwracany <xref:System.Collections.Hashtable>z. Ze względu na wydajność implementacja programu <xref:System.Object.GetHashCode%2A> może się zmieniać między wersjami środowiska uruchomieniowego, więc kolizje, które mogą nie wystąpić w jednej wersji, mogą wystąpić w kolejnych wersjach. Włącz tę funkcję MDA, aby sprawdzić, czy kod ma błędy w przypadku kolizji kodów mieszania. Po włączeniu tego MDA powoduje, że <xref:System.Object.GetHashCode%2A> Metoda zwraca wartość 0, co koliduje ze wszystkimi kodami mieszania. Jedynym efektem włączenia tego pakietu w programie jest to, że program działa wolniej.  
  
 Kolejność wyliczania z programu <xref:System.Collections.Hashtable> może ulec zmianie z jednej wersji środowiska uruchomieniowego na inną, jeśli algorytm używany do obliczania kodów skrótów dla zmiany klucza. Aby sprawdzić, czy program pobrał zależność od kolejności wyliczania kluczy lub wartości z tabeli skrótów, można włączyć to zdarzenie MDA.  
  
## <a name="resolution"></a>Rozwiązanie  
 Nigdy nie używaj kodów skrótu jako substytutu dla tożsamości obiektu. Zaimplementuj przesłonięcie <xref:System.Object.Equals%2A?displayProperty=nameWithType> metody, aby nie porównywać kodów skrótów.  
  
 Nie należy tworzyć zależności względem kolejności wyliczeń kluczy lub wartości w tabelach skrótów.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Aplikacje działają wolniej, gdy to MDA jest włączone. To zdarzenie MDA po prostu pobiera zwrócony kod skrótu, a zamiast tego zwraca resztę przy poddzieleniu przez moduł.  
  
## <a name="output"></a>Dane wyjściowe  
 Brak danych wyjściowych dla tego MDA.  
  
## <a name="configuration"></a>Konfiguracja  
 Ten `modulus` atrybut określa moduł używany w kodzie skrótu. Wartość domyślna to 1.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
