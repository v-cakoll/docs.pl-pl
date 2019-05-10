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
ms.openlocfilehash: 9b1223839be3747b04810d6b5bd131733c41631f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614389"
---
# <a name="moduloobjecthashcode-mda"></a>moduloObjectHashcode MDA
`moduloObjectHashcode` Zarządzanego Asystenta debugowania (MDA) zmienia zachowanie <xref:System.Object> klasy w celu wykonania modulo operacja zwracane przez wartość skrótu <xref:System.Object.GetHashCode%2A> metody. Modulo domyślny dla to zdarzenie MDA wynosi 1, co powoduje, że <xref:System.Object.GetHashCode%2A> do zwrócenia 0 dla wszystkich obiektów.  
  
## <a name="symptoms"></a>Symptomy  
 Po przeniesieniu do nowej wersji środowiska uruchomieniowego języka wspólnego (CLR), program nie jest już działa prawidłowo:  
  
- Program będzie niedługo niewłaściwym obiektem z <xref:System.Collections.Hashtable>.  
  
- Kolejność wyliczania z <xref:System.Collections.Hashtable> zmieniło przerwanie wykonywania programu.  
  
- Dwa obiekty, które umożliwiają równe już nie są równe.  
  
- Dwa obiekty, które są używane, nie są równe, teraz są równe.  
  
## <a name="cause"></a>Przyczyna  
 Program może być wprowadzenie niewłaściwym obiektem z <xref:System.Collections.Hashtable> ponieważ implementacja <xref:System.Object.Equals%2A> metodę w klasie klucz do <xref:System.Collections.Hashtable> testuje pod kątem równości obiektów przez porównanie wyników wywołanie <xref:System.Object.GetHashCode%2A> — metoda . Kody skrótów nie powinien umożliwia testowanie dla równości obiektu, ponieważ dwa obiekty mogą mieć tę samą wartość skrótu, nawet jeśli ich odpowiednich pól mają różne wartości. Te konflikty kod skrótu, występować sporadycznie w praktyce. Efekt ten ma na <xref:System.Collections.Hashtable> wyszukiwania jest wyświetlane dwa klucze, które nie są takie same, równe i nieprawidłowy obiekt jest zwracany z <xref:System.Collections.Hashtable>. Ze względu na wydajność wdrożenia <xref:System.Object.GetHashCode%2A> może się zmieniać między wersjami środowiska uruchomieniowego, więc mogą wystąpić konflikty, które nie mogą wystąpić w jednej wersji, w kolejnych wersjach. Włącz to zdarzenie MDA sprawdzić, czy kod ma błędy, gdy kolizji kodów wartości skrótu. Po włączeniu to zdarzenie MDA powoduje, że <xref:System.Object.GetHashCode%2A> metody zwracają 0, co wszystkie kody skrótów kolizji. Jedynie wpływ Włączanie to zdarzenie MDA powinien już z programu jest spowolnienie działania Twojego programu.  
  
 Kolejność wyliczania z <xref:System.Collections.Hashtable> mogą ulec zmianie z jednej wersji środowiska uruchomieniowego, jeśli inny algorytm używany do obliczania kodów skrótu dla zmian klucza. Aby sprawdzić, czy program miało zależności kolejności wyliczenie kluczy i wartości z tabeli wyznaczania wartości skrótu, aby umożliwić to zdarzenie MDA.  
  
## <a name="resolution"></a>Rozwiązanie  
 Nigdy nie używaj kody skrótów zastępuje tożsamość obiektu. Implementowanie zastępowania metody <xref:System.Object.Equals%2A?displayProperty=nameWithType> metoda porównuje kodów wartości skrótu.  
  
 Nie należy tworzyć zależności w kolejności wyliczenia o kluczy ani wartości w tabelach wyznaczania wartości skrótu.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Aplikacje działają wolniej, po włączeniu to zdarzenie MDA. To zdarzenie MDA po prostu przyjmuje skrótu, który będzie zwracany i zamiast tego zwraca resztę z dzielenia podzielone przez moduł.  
  
## <a name="output"></a>Dane wyjściowe  
 Nie ma żadnych danych wyjściowych dla tego MDA.  
  
## <a name="configuration"></a>Konfiguracja  
 `modulus` Atrybut określa modulo na wartość skrótu. Wartość domyślna to 1.  
  
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
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
