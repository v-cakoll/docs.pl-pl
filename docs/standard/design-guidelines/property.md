---
title: Projekt właściwości
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
ms.openlocfilehash: c49b42ab369ace582c76d7f326da309415e8c45b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291945"
---
# <a name="property-design"></a>Projekt właściwości
Chociaż właściwości są technicznie bardzo podobne do metod, są one bardzo odmienne pod względem scenariuszy użycia. Powinny być one widoczne jako pola inteligentne. Mają one składnię wywołującą pól i elastyczność metod.

 ✔️ utworzyć właściwości tylko DO pobrania, jeśli obiekt wywołujący nie powinien mieć możliwości zmiany wartości właściwości.

 Należy pamiętać, że jeśli typ właściwości jest modyfikowalnym typem odwołania, wartość właściwości można zmienić, nawet jeśli właściwość jest tylko do odczytu.

 ❌Nie udostępniaj właściwości "Set-Only" ani właściwości z Setter, która ma szerszy dostęp niż metoda pobierająca.

 Na przykład nie należy używać właściwości z publiczną setter i chronioną metodę pobierającą.

 Jeśli nie można podać metody pobierającej właściwość, zamiast tego należy zaimplementować funkcję jako metodę. Rozważ uruchomienie nazwy metody z `Set` i po nazwie właściwości. Na przykład <xref:System.AppDomain> ma metodę o nazwie, która `SetCachePath` nie ma właściwości "Set-Only" `CachePath` .

 ✔️ zapewnić rozsądne wartości domyślne dla wszystkich właściwości, co gwarantuje, że wartości domyślne nie powodują, że w żadnym przypadku nie są napoważny zabezpieczenia ani nieefektywny kod.

 ✔️ Zezwalaj na ustawianie właściwości w dowolnej kolejności, nawet jeśli spowoduje to tymczasowy nieprawidłowy stan obiektu.

 Jest ona wspólna dla dwóch lub więcej właściwości, które mają być powiązane z punktem, w którym niektóre wartości jednej właściwości mogą być nieprawidłowe z uwzględnieniem wartości innych właściwości w tym samym obiekcie. W takich przypadkach wyjątki, które wynikają z nieprawidłowego stanu, powinny być odroczone do momentu, gdy właściwości międzypowiązane są rzeczywiście używane razem z obiektem.

 ✔️ zachować poprzedniej wartości, jeśli Metoda ustawiająca Właściwość zgłosi wyjątek.

 ❌UNIKAj zgłaszania wyjątków z metod pobierających właściwości.

 Metody pobierające właściwości powinny być prostymi operacjami i nie powinny mieć żadnych warunków wstępnych. Jeśli metoda pobierająca może zgłosić wyjątek, prawdopodobnie powinna zostać przeprojektowana tak, aby była metodą. Należy zauważyć, że ta zasada nie ma zastosowania do indeksatorów, w przypadku których oczekujemy wyjątków w wyniku walidacji argumentów.

### <a name="indexed-property-design"></a>Projekt właściwości indeksowanej
 Indeksowana właściwość jest właściwością specjalną, która może mieć parametry i może być wywoływana przy użyciu specjalnej składni podobnej do indeksowania tablicy.

 Właściwości indeksowane są często określane jako indeksatory. Indeksatory powinny być używane tylko w interfejsach API, które zapewniają dostęp do elementów w kolekcji logicznej. Na przykład ciąg jest kolekcją znaków, a indeksator <xref:System.String?displayProperty=nameWithType> został dodany w celu uzyskania dostępu do jego znaków.

 ✔️ Rozważ użycie indeksatorów, aby zapewnić dostęp do danych przechowywanych w tablicy wewnętrznej.

 ✔️ Rozważ dostarczenie indeksatorów dla typów reprezentujących kolekcje elementów.

 ❌Należy unikać używania właściwości indeksowanych z więcej niż jednym parametrem.

 Jeśli projekt wymaga wielu parametrów, należy rozważyć, czy właściwość naprawdę reprezentuje metodę dostępu do kolekcji logicznej. Jeśli tak nie jest, zamiast tego użyj metod. Rozważ uruchomienie nazwy metody z `Get` lub `Set` .

 ❌Unikaj indeksatorów z typami parametrów innymi niż <xref:System.Int32?displayProperty=nameWithType> , <xref:System.Int64?displayProperty=nameWithType> , <xref:System.String?displayProperty=nameWithType> , <xref:System.Object?displayProperty=nameWithType> lub wyliczeniem.

 Jeśli projekt wymaga innych typów parametrów, należy silnie oszacować, czy interfejs API naprawdę reprezentuje metodę dostępu do logicznej kolekcji. Jeśli tak nie jest, użyj metody. Rozważ uruchomienie nazwy metody z `Get` lub `Set` .

 ✔️ należy używać nazwy `Item` indeksowanych właściwości, chyba że jest to wyraźnie lepsza nazwa (np. <xref:System.String.Chars%2A> Właściwość na `System.String` ).

 W języku C# Indeksatory są domyślnie nazwanymi elementami. <xref:System.Runtime.CompilerServices.IndexerNameAttribute>Można użyć, aby dostosować tę nazwę.

 ❌NIE należy podawać zarówno indeksatora, jak i metod, które są semantycznie równoważne.

 ❌Nie udostępniaj więcej niż jednej rodziny przeciążonych indeksatorów w jednym typie.

 Jest to wymuszane przez kompilator języka C#.

 ❌NIE używaj właściwości indeksowanych innych niż domyślne.

 Jest to wymuszane przez kompilator języka C#.

### <a name="property-change-notification-events"></a>Zdarzenia powiadamiania o zmianie właściwości
 Czasami warto podać zdarzenie powiadamiające użytkownika o zmianach w wartości właściwości. Na przykład `System.Windows.Forms.Control` wywołuje `TextChanged` zdarzenie po zmianie wartości jego `Text` właściwości.

 ✔️ ROZWAŻYĆ podnoszenie poziomu powiadomień o zmianach, gdy wartości właściwości w interfejsach API wysokiego poziomu (zazwyczaj składniki projektanta) są modyfikowane.

 Jeśli istnieje dobry scenariusz dla użytkownika, aby wiedzieć, kiedy zmienia się właściwość obiektu, obiekt powinien zgłosić zdarzenie zmiany powiadomienia dla właściwości.

 Nie jest jednak mało prawdopodobne, aby wywoływać te zdarzenia dla interfejsów API niskiego poziomu, takich jak typy podstawowe lub kolekcje. Na przykład <xref:System.Collections.Generic.List%601> nie będzie zgłaszać takich zdarzeń, gdy nowy element zostanie dodany do listy i `Count` Zmiana właściwości.

 ✔️ ROZWAŻYĆ podnoszenie poziomu powiadomień o zmianach, gdy wartość właściwości zostanie zmieniona za pośrednictwem sił zewnętrznych.

 Jeśli wartość właściwości zostanie zmieniona za pośrednictwem niektórych zewnętrznych sił (w inny sposób niż wywoływanie metod w obiekcie), zdarzenia zdarzeń wskazują deweloperowi, że wartość zmienia się i została zmieniona. Dobrym przykładem jest `Text` Właściwość kontrolki pola tekstowego. Gdy użytkownik wpisze tekst w `TextBox` , wartość właściwości jest automatycznie zmieniana.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania elementów członkowskich](member.md)
- [Wskazówki dotyczące projektowania struktury](index.md)
