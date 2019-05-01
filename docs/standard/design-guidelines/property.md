---
title: Projekt właściwości
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
author: KrzysztofCwalina
ms.openlocfilehash: e4ed4fd39a9ebd63b9d5dbff38dc15647d65934f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026321"
---
# <a name="property-design"></a>Projekt właściwości
Choć z technicznego punktu widzenia są bardzo podobne do metody właściwości są zupełnie różne pod względem scenariusze ich użycia. Powinny one widoczne, jako pola inteligentne. Mają one, składnia wywoływania pól i swobodne korzystanie z metod.  
  
 **✓ DO** utworzenie właściwości tylko do pobrania, jeśli element wywołujący nie ma być można zmienić wartości właściwości.  
  
 Należy pamiętać, że jeśli typ właściwość jest typu referencji zmiennej, nawet jeśli właściwość jest tylko do pobierania można zmienić wartości właściwości.  
  
 **X DO NOT** Podaj setter o dostępności szerszym niż metoda pobierająca właściwości tylko do zestawu lub właściwości.  
  
 Na przykład nie za pomocą właściwości publicznej metody ustawiającej ani pobierającej chronionych.  
  
 Jeśli metoda pobierająca właściwości nie można podać, należy zaimplementować funkcje jako metody. Rozważ rozpoczęcie nazwę metody z `Set` i postępuj zgodnie ze co będzie mieć nazwę właściwości. Na przykład <xref:System.AppDomain> ma metodę o nazwie `SetCachePath` zamiast właściwość tylko do zestawu o nazwie `CachePath`.  
  
 **✓ DO** podać za pośrednictwem domyślne wartości dla wszystkich właściwości, zapewniając, że wartości domyślne nie powodują luka w zabezpieczeniach lub poważny niewydajny kod.  
  
 **✓ DO** umożliwia właściwości można ustawić w dowolnej kolejności, nawet jeśli spowoduje to tymczasowe nieprawidłowy stan obiektu.  
  
 To częsty problem w dwóch lub więcej właściwości, aby być powiązane ze sobą do punktu, w której niektóre wartości w jedną właściwość może być nieprawidłowy podane wartości innych właściwości dla tego samego obiektu. W takich przypadkach wyjątki wynikłe ze nieprawidłowy stan powinien zostać odroczony do momentu wzajemnie powiązanych właściwości są rzeczywiście używane razem z obiektu.  
  
 **✓ DO** zachować poprzedniej wartości, jeśli metody ustawiającej właściwość zgłasza wyjątek.  
  
 **X AVOID** zgłaszanie wyjątków z pobierających właściwości.  
  
 Metody pobierające właściwości powinny być proste operacje i nie powinny mieć wszystkie warunki wstępne. Jeśli metoda pobierająca może zgłosić wyjątek, prawdopodobnie należy przeprojektowany jako metodę. Należy zauważyć, że ta zasada nie ma zastosowania do indeksatory, w którym oczekujemy, że wyjątki w wyniku sprawdzania poprawności argumentów.  
  
### <a name="indexed-property-design"></a>Właściwość indeksowana projektu  
 Indeksowana właściwość jest właściwością specjalne, która może mieć parametrów i może być wywoływana przy użyciu specjalnej składni podobnie jak indeksowanie tablicy.  
  
 Właściwości indeksowane są często nazywane indeksatorów. Indeksatory należy używać tylko w przypadku interfejsów API, które zapewniają dostęp do elementów w kolekcji logiczne. Na przykład ciąg to zbiór znaków i indeksatora w <xref:System.String?displayProperty=nameWithType> została dodana do dostęp do jego znaków.  
  
 **✓ CONSIDER** przy użyciu indeksatorów w celu zapewnienia dostępu do danych przechowywanych w tablicy wewnętrznej.  
  
 **✓ CONSIDER** udostępnia indeksatory na typy reprezentujące kolekcje elementów.  
  
 **X AVOID** przy użyciu indeksowane właściwości z więcej niż jeden parametr.  
  
 Jeśli projekt wymaga wielu parametrów, ponowne rozpatrzenie czy właściwość reprezentuje jest naprawdę akcesora czyli logicznej kolekcji. Jeśli nie, należy użyć metody. Rozważ rozpoczęcie nazwę metody z `Get` lub `Set`.  
  
 **X AVOID** indeksatory z typami parametrów innych niż <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, lub wyliczenia.  
  
 Jeśli projekt wymaga innych typów lub parametrów, a silnie ponownie oceń czy interfejs API reprezentuje jest naprawdę akcesora czyli logicznej kolekcji. Jeśli nie, należy użyć metody. Rozważ rozpoczęcie nazwę metody z `Get` lub `Set`.  
  
 **✓ DO** Użyj nazwy `Item` dla właściwości indeksowanych, chyba że istnieje lepsze oczywiście nazwa (np. zobacz <xref:System.String.Chars%2A> właściwość `System.String`).  
  
 W języku C# indeksatory są domyślnie nazwanego elementu. <xref:System.Runtime.CompilerServices.IndexerNameAttribute> Można dostosować tę nazwę.  
  
 **X DO NOT** zapewniają zarówno indeksatora, jak i metody, które są semantycznie równoważne.  
  
 **X DO NOT** zapewniają więcej niż jednej rodziny przeciążone indeksatorów w jednym typie.  
  
 Ta wartość jest wymuszana przez kompilator języka C#.  
  
 **X DO NOT** niestandardowy użycie właściwości indeksowanych.  
  
 Ta wartość jest wymuszana przez kompilator języka C#.  
  
### <a name="property-change-notification-events"></a>Zdarzenia powiadomień zmiany właściwości  
 Czasami przydatne jest zapewnienie zdarzenie powiadamiania użytkownika o zmianach w wartości właściwości. Na przykład `System.Windows.Forms.Control` zgłasza `TextChanged` zdarzeń po wartości jego `Text` właściwości została zmieniona.  
  
 **✓ CONSIDER** wywoływanie zmienić zdarzenia powiadomień po zmodyfikowaniu wartości właściwości ogólnych interfejsów API (zazwyczaj projektanta składników).  
  
 W przypadku dobrej scenariusz dla użytkownika dowiedzieć się, gdy zmienia się właściwość obiektu, obiekt powinna podnieść zdarzenia powiadomienia o zmianie właściwości.  
  
 Jest mało prawdopodobne, aby być warte włożonej obciążenie, które można wywoływać zdarzenia, takiego niskiego poziomu interfejsy API, takich jak typy podstawowe lub kolekcji. Na przykład <xref:System.Collections.Generic.List%601> nie zainicjowałaby takie zdarzenia, gdy nowy element zostanie dodany do listy i `Count` zmiany właściwości.  
  
 **✓ CONSIDER** wywoływanie zmienić zdarzenia powiadomień za pomocą zewnętrznego wymusza po zmianie wartości właściwości.  
  
 Jeśli wartość właściwości zmieni się za pośrednictwem niektórych siły zewnętrzne (w sposób inny niż przez wywołanie metody dla obiektu), należy zgłosić zdarzenia wskazują dla dewelopera, że wartość zmienia się i został zmieniony. Dobrym przykładem jest `Text` właściwość kontrolkę pola tekstowego. Gdy użytkownik wpisze tekst w `TextBox`, automatycznie ulega zmianie wartość właściwości.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
