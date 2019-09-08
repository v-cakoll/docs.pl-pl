---
title: Zabezpieczenia (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
ms.openlocfilehash: d6f00fccb0ea2f49c19b640e31d96e575c0d48b9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782786"
---
# <a name="security-linq-to-dataset"></a>Zabezpieczenia (LINQ to DataSet)
W tym temacie omówiono problemy z zabezpieczeniami w programie LINQ to DataSet.  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>Przekazywanie zapytania do niezaufanego składnika  
 Zapytanie LINQ to DataSet może być sformułowane w jednym punkcie programu i wykonywane w innym. W punkcie, w którym zapytanie jest sformułowane, zapytanie może odwoływać się do każdego elementu, który jest widoczny w tym punkcie, takich jak prywatne elementy członkowskie klasy, do której należy Metoda wywołująca, lub symbole reprezentujące zmienne lokalne/argumenty. W czasie wykonywania zapytanie będzie efektywnie mogło uzyskać dostęp do tych elementów członkowskich, do których odwołuje się zapytanie podczas formowania, nawet jeśli kod wywołujący nie ma wglądu w te elementy. Kod, który wykonuje zapytanie nie ma dowolnie dodanej widoczności, nie może wybrać, do czego uzyskać dostęp. Będzie ona mogła uzyskać dostęp do ściśle określonych zapytań i tylko za pomocą samego zapytania.  
  
 Oznacza to, że przekazując odwołanie do zapytania do innego fragmentu kodu, składnik otrzymujący zapytanie jest zaufany z dostępem do wszystkich publicznych i prywatnych członków, do których odwołuje się zapytanie. Ogólnie rzecz biorąc, zapytania LINQ to DataSet nie powinny być przesyłane do niezaufanych składników, chyba że zapytanie zostało starannie skonstruowane, tak aby nie ujawniać informacji, które powinny być przechowywane w trybie prywatnym.  
  
## <a name="external-input"></a>Dane wejściowe zewnętrznego  
 Aplikacje często pobierają zewnętrzne dane wejściowe (od użytkownika lub innego agenta zewnętrznego) i wykonują działania na podstawie tych danych wejściowych.  W przypadku LINQ to DataSet aplikacja może utworzyć zapytanie w określony sposób na podstawie zewnętrznych danych wejściowych lub użyć zewnętrznych danych wejściowych w zapytaniu. Zapytania LINQ to DataSet akceptują parametry wszędzie, gdzie literały są akceptowane. Deweloperzy aplikacji powinni używać zapytań parametrycznych, a nie wstrzyknąć literałów z zewnętrznego agenta bezpośrednio do zapytania.  
  
 Wszelkie dane wejściowe bezpośrednio lub pośrednio pochodzące od użytkownika lub zewnętrznego agenta mogą mieć zawartość, która wykorzystuje składnię języka docelowego w celu wykonywania nieautoryzowanych akcji. Jest to nazywane atakami polegającymi na iniekcji kodu SQL, nazwami po wzorcu ataku, gdzie językiem docelowym jest Transact-SQL. Dane wprowadzane przez użytkownika bezpośrednio do zapytania są używane w celu usunięcia tabeli bazy danych, spowodowania odmowy usługi lub zmiany charakteru wykonywanej operacji. Chociaż kompozycja zapytania jest możliwa w LINQ to DataSet, jest wykonywana za pomocą interfejsu API modelu obiektów. Zapytania LINQ to DataSet nie są tworzone przy użyciu operacji manipulowania ciągiem lub łączenia, ponieważ są one w języku Transact-SQL i nie są podatne na ataki z iniekcją SQL w tradycyjnym sensie.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania](programming-guide-linq-to-dataset.md)
