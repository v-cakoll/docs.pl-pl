---
title: Nazwy składowych typu
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
ms.openlocfilehash: 87cf793229cfc7d8d0547af935369a3febee41a3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290191"
---
# <a name="names-of-type-members"></a>Nazwy składowych typu
Typy składowe są elementami członkowskimi: metodami, właściwościami, zdarzeniami, konstruktorami i polami. W poniższych sekcjach opisano wskazówki dotyczące nazewnictwa elementów członkowskich typu.

## <a name="names-of-methods"></a>Nazwy metod
 Ponieważ metody są metodą podjęcia działania, wskazówki dotyczące projektowania wymagają, aby nazwy metod były czasownikami lub wyrażeniami czasownikowymi. Poniższe wytyczne umożliwiają również odróżnianie nazw metod od nazw właściwości i typów, które są frazami rzeczownikmi lub przymiotnikami.

 ✔️ NALEŻY nadać metodom nazwy, które są czasownikami lub czasownikami zleceń.

```csharp
public class String {
    public int CompareTo(...);
    public string[] Split(...);
    public string Trim();
}
```

## <a name="names-of-properties"></a>Nazwy właściwości
 W przeciwieństwie do innych elementów członkowskich, właściwości powinny zawierać frazę rzeczowników lub nazwy przymiotników. Oznacza to, że Właściwość odwołuje się do danych, a nazwa właściwości odzwierciedla to. PascalCasing jest zawsze używana dla nazw właściwości.

 ✔️ Właściwości nazwy przy użyciu rzeczownika, frazy rzeczowników lub przymiotniku.

 ❌NIE mają właściwości, które pasują do nazwy metod "Get", tak jak w poniższym przykładzie:

 `public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`

 Ten wzorzec zazwyczaj wskazuje, że właściwość powinna być w rzeczywistości metodą.

 ✔️ DO właściwości kolekcji nazw z frazą w liczbie mnogiej opisującą elementy w kolekcji, zamiast używać pojedynczej frazy, a po niej "list" lub "Collection".

 ✔️ NALEŻY nazwać właściwości logiczne z wyrażeniem potwierdzającym ( `CanSeek` zamiast `CantSeek` ). Opcjonalnie można również prefiksować właściwości logiczne z "is", "może" lub "ma", ale tylko wtedy, gdy dodaje wartość.

 ✔️ ROZWAŻYĆ nadanie właściwości takiej samej nazwy jak jej typ.

 Na przykład następująca Właściwość prawidłowo pobiera i ustawia wartość wyliczenia o nazwie `Color` , więc właściwość ma nazwę `Color` :

```csharp
public enum Color {...}
public class Control {
    public Color Color { get {...} set {...} }
}
```

## <a name="names-of-events"></a>Nazwy zdarzeń
 Zdarzenia zawsze odwołują się do niektórych akcji, takich, które są wykonywane lub takie, które wystąpiły. W związku z tym, podobnie jak w przypadku metod, zdarzenia są nazwane przy użyciu czasowników, a w celu wskazania czasu, gdy zdarzenie jest zgłaszane, używana jest wartość zlecenia.

 ✔️ NALEŻY nazwać zdarzenia za pomocą czasownika lub wyrażenia orzeczenia.

 Przykłady obejmują `Clicked` , `Painting` , `DroppedDown` , i tak dalej.

 ✔️ NALEŻY udzielić nazw zdarzeń z koncepcją przed i po, przy użyciu obecnych i ostatnich dziesiątek.

 Na przykład zdarzenie zamknięcia, które jest wywoływane przed zamknięciem okna, zostanie wywołane `Closing` , a jeden, który jest wywoływany po zamknięciu okna, zostanie wywołany `Closed` .

 ❌NIE używaj "Before" lub "After" prefiksów ani przyrostków, aby wskazać zdarzenia poprzedzające i końcowe. Użyj obecnych i ostatnich dziesiątek tak samo, jak zostało to opisane.

 ✔️ obsługi zdarzeń nazw (delegatów używanych jako typy zdarzeń) przy użyciu sufiksu "EventHandler", jak pokazano w następującym przykładzie:

 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`

 ✔️ używać dwóch parametrów o nazwach `sender` i `e` w obsłudze zdarzeń.

 Parametr Sender reprezentuje obiekt, który spowodował zdarzenie. Parametr nadawcy jest zazwyczaj typu `object` , nawet jeśli można użyć bardziej określonego typu.

 ✔️ NALEŻY nazwać klasy argumentów zdarzeń z sufiksem "EventArgs".

## <a name="names-of-fields"></a>Nazwy pól
 Wskazówki dotyczące nazewnictwa pól mają zastosowanie do statycznych pól publicznych i chronionych. Pola wewnętrzne i prywatne nie są objęte wskazówkami, a pola Public lub Protected instance są niedozwolone w [wytycznych dotyczących projektowania elementu członkowskiego](member.md).

 ✔️ używać PascalCasing w nazwach pól.

 ✔️ nazwy pól przy użyciu rzeczownika, frazy rzeczowników lub przymiotniku.

 ❌NIE należy używać prefiksu dla nazw pól.

 Na przykład nie należy używać "g_" lub "s_" do wskazania pól statycznych.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania struktury](index.md)
- [Wskazówki dotyczące nazewnictwa](naming-guidelines.md)
