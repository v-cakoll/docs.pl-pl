---
title: Właściwości projektu
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a4aec965753fe8f89b8bd89469f8dc5739a6a7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="property-design"></a>Właściwości projektu
Właściwości są technicznie bardzo podobna do metody, są one zupełnie różne pod względem ich scenariusze użycia. Powinny one widoczne jako inteligentny pola. Mają one składnia wywoływania pól i elastyczności metody.  
  
 **CZY ✓** utworzenie właściwości tylko do pobrania, jeśli element wywołujący nie ma być można zmienić wartości właściwości.  
  
 Należy pamiętać, że jeśli typ właściwości jest typem referencyjnym modyfikowalna, wartość właściwości jest możliwa, nawet jeśli właściwość jest tylko do pobrania.  
  
 **X nie** Podaj setter o dostępności szerszym niż metoda pobierająca właściwości tylko do zestawu lub właściwości.  
  
 Na przykład nie należy używać właściwości z publicznej metody ustawiającej i chronione metody pobierającej.  
  
 Jeśli metoda pobierająca właściwości nie można podać, należy zaimplementować tę funkcję, co metoda. Należy rozważyć uruchomienie nazwę metody z `Set` i postępuj zgodnie z co może mieć nosi nazwę właściwości. Na przykład <xref:System.AppDomain> ma metodę o nazwie `SetCachePath` zamiast właściwość tylko do zestawu o nazwie `CachePath`.  
  
 **CZY ✓** podać za pośrednictwem domyślne wartości dla wszystkich właściwości, zapewniając, że wartości domyślne nie powodują luka w zabezpieczeniach lub poważny niewydajny kod.  
  
 **CZY ✓** umożliwia właściwości można ustawić w dowolnej kolejności, nawet jeśli spowoduje to tymczasowe nieprawidłowy stan obiektu.  
  
 Bardzo często dwóch lub więcej właściwości do punktu, w której niektóre wartości jedną właściwość może być nieprawidłowy powiązanych podane wartości innych właściwości w tym samym obiekcie. W takich przypadkach należy odroczyć wyjątki wynikające z nieprawidłowym stanie dopóki wzajemnie powiązanych właściwości są rzeczywiście używane razem z obiektu.  
  
 **CZY ✓** zachować poprzedniej wartości, jeśli metody ustawiającej właściwość zgłasza wyjątek.  
  
 **X należy UNIKAĆ** zgłaszanie wyjątków z pobierających właściwości.  
  
 Metody pobierające właściwości powinny być proste operacje i nie powinny mieć wszystkie warunki wstępne. Jeśli metoda pobierająca może zgłosić wyjątek, prawdopodobnie powinien przeprojektowany jako metodę. Należy zauważyć, że ta zasada nie ma zastosowania do indeksatorów, gdzie oczekiwane wyjątki w wyniku sprawdzania poprawności argumentów.  
  
### <a name="indexed-property-design"></a>Właściwość indeksowana projektu  
 Właściwość indeksowana jest specjalne właściwości, która może mieć parametrów i może być wywołany z specjalne składnię indeksowanie tablicy.  
  
 Właściwości indeksowane są często nazywane indeksatorów. Indeksatory powinna być używana tylko w interfejsów API, które zapewniają dostęp do elementów w kolekcji logiczne. Na przykład ciąg to zbiór znaków i indeksatora na <xref:System.String?displayProperty=nameWithType> został dodany do dostęp do jego znaków.  
  
 **ROZWAŻ ✓** przy użyciu indeksatorów w celu zapewnienia dostępu do danych przechowywanych w tablicy wewnętrznej.  
  
 **ROZWAŻ ✓** udostępnia indeksatory na typy reprezentujące kolekcje elementów.  
  
 **X należy UNIKAĆ** przy użyciu indeksowane właściwości z więcej niż jeden parametr.  
  
 Jeśli projekt wymaga kilku parametrów, rozważenia, czy właściwość naprawdę reprezentuje metody dostępu do kolekcji logiczne. Jeśli nie, należy użyć metody. Należy rozważyć uruchomienie nazwę metody z `Get` lub `Set`.  
  
 **X należy UNIKAĆ** indeksatory z typami parametrów innych niż <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, lub wyliczenia.  
  
 Jeśli projekt wymaga innych typów parametrów, a silnie obliczyć ponownie czy naprawdę interfejsu API reprezentuje metody dostępu do kolekcji logiczne. Jeśli nie, należy użyć metody. Należy rozważyć uruchomienie nazwę metody z `Get` lub `Set`.  
  
 **CZY ✓** Użyj nazwy `Item` dla właściwości indeksowanych, chyba że istnieje lepsze oczywiście nazwa (np. zobacz <xref:System.String.Chars%2A> właściwość `System.String`).  
  
 W języku C# indeksatory są domyślnie nazwanego elementu. <xref:System.Runtime.CompilerServices.IndexerNameAttribute> Można dostosować tę nazwę.  
  
 **X nie** zapewniają zarówno indeksatora, jak i metody, które są semantycznie równoważne.  
  
 **X nie** zapewniają więcej niż jednej rodziny przeciążone indeksatorów w jednym typie.  
  
 Ta wartość jest wymuszana przez kompilator języka C#.  
  
 **X nie** niestandardowy użycie właściwości indeksowanych.  
  
 Ta wartość jest wymuszana przez kompilator języka C#.  
  
### <a name="property-change-notification-events"></a>Zdarzenia powiadomień zmiany właściwości  
 Czasami jest wprowadzenie zdarzenie powiadomienia użytkownika o zmianach w wartości właściwości. Na przykład `System.Windows.Forms.Control` zgłasza `TextChanged` zdarzeń po wartości jego `Text` właściwość zostanie zmieniona.  
  
 **ROZWAŻ ✓** wywoływanie zmienić zdarzenia powiadomień po zmodyfikowaniu wartości właściwości ogólnych interfejsów API (zazwyczaj projektanta składników).  
  
 W przypadku scenariusza dobrej dla użytkownika dowiedzieć się, gdy Trwa zmienianie właściwości obiektu, obiekt powinien podnieść zdarzenia powiadomień zmiany właściwości.  
  
 Jednak jest mało prawdopodobne, aby warto obciążenie wywołania takich zdarzeń dla interfejsów API niskiego poziomu, takich jak typy podstawowe lub kolekcji. Na przykład <xref:System.Collections.Generic.List%601> nie wywołałoby takie zdarzenia po dodaniu nowego elementu do listy i `Count` zmiany właściwości.  
  
 **ROZWAŻ ✓** wywoływanie zmienić zdarzenia powiadomień za pomocą zewnętrznego wymusza po zmianie wartości właściwości.  
  
 W przypadku zmiany wartości właściwości za pośrednictwem niektórych siły zewnętrzne (w sposób inny niż przez wywołanie metody obiektu), zgłoś zdarzenia wskazują deweloperowi, że wartość zmienia się i został zmieniony. Dobrym przykładem jest `Text` właściwości formantu pola tekstowego. Gdy użytkownik wpisze tekst w `TextBox`, automatycznie zmienia się wartość właściwości.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
