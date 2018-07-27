---
title: Nazwy elementów członkowskich typu
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25fe93b63c518f54ee72300f26dfcb3f3ad21d76
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2018
ms.locfileid: "33575352"
---
# <a name="names-of-type-members"></a>Nazwy elementów członkowskich typu
Typy składają się z elementów członkowskich: metody, właściwości, zdarzenia, konstruktory i pola. W poniższych sekcjach opisano zasady nazewnictwa elementów członkowskich typu.  
  
## <a name="names-of-methods"></a>Nazwy metody  
 Ponieważ metody oznacza, że podjęcia działań, wytyczne dotyczące projektowania wymagają nazwy metod zleceń i fraz zlecenie. Następujące ta wytyczna również służy do odróżnienia nazwy metod nazwy właściwości i typów, które są rzeczownik lub przymiotnik fraz.  
  
 **CZY ✓** Nadaj nazwy metody, które mogą lub fraz zlecenie.  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a>Nazwy właściwości  
 W przeciwieństwie do innych członków właściwości powinien być podawany przymiotników nazw lub frazy rzeczownik. To, ponieważ właściwość odnosi się do danych i nazwę właściwości odzwierciedlała to. PascalCasing jest zawsze używany dla nazwy właściwości.  
  
 **CZY ✓** nazwę właściwości, za pomocą rzeczownik, rzeczownik frazy lub przymiotnik.  
  
 **X nie** mają właściwości, które zgodna z nazwą metody "Get", jak w poniższym przykładzie:  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 Ten wzorzec zazwyczaj wskazuje, czy właściwość naprawdę powinna być metody.  
  
 **CZY ✓** nazwy właściwości kolekcji o liczbie mnogiej frazę opisujące elementy w kolekcji, zamiast korzystać z pojedynczej frazy, a następnie "List" lub "Collection".  
  
 **CZY ✓** nazwy właściwości logiczne z frazą wyraził (`CanSeek` zamiast `CantSeek`). Opcjonalnie można także prefiks właściwości logiczne "Is", "możliwości" lub "Ma," tylko wtedy, gdy dodatkowe korzyści.  
  
 **ROZWAŻ ✓** zapewnia taką samą nazwę jak jego typ właściwości.  
  
 Na przykład, następująca właściwość poprawnie pobiera i ustawia wartość wyliczenia o nazwie `Color`, więc nosi nazwę właściwości `Color`:  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a>Nazwy zdarzeń  
 Zdarzenia zawsze odwołuje się do niektórych akcji, który jest występuje albo, który wystąpił. W związku z tym podobnie jak w przypadku metod, zdarzeń są nazywane zleceń i czasu teraźniejszego zlecenia służy do wskazywania czasu, gdy zdarzenie jest wywoływane.  
  
 **CZY ✓** nazwy zdarzeń za pomocą zlecenie lub zlecenia frazę.  
  
 Przykłady obejmują `Clicked`, `Painting`, `DroppedDown`i tak dalej.  
  
 **CZY ✓** nadać nazwy zdarzenia przy użyciu koncepcji przed i po nim, za pomocą obecny i czasy w przeszłości.  
  
 Na przykład, czy można wywołać Zamknij zdarzenie, które jest wywoływane przed zamknięciem okna `Closing`, i może być wywoływana taki, który jest uruchamiany po zamknięciu okna `Closed`.  
  
 **X nie** Użyj "Before" lub "After" prefiksy lub postfixes, aby wskazać, przed i po zdarzenia. Użyj obecne i czasy ostatnich, jak opisano powyżej.  
  
 **CZY ✓** nazwy programów obsługi zdarzeń (używany jako typy zdarzeń delegaty) wraz z sufiksem "EventHandler", jak pokazano w poniższym przykładzie:  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 **CZY ✓** korzystanie z dwóch parametrów o nazwie `sender` i `e` w procedurze obsługi zdarzeń.  
  
 Parametr sender reprezentuje obiekt, który spowodował zdarzenie. Parametr sender jest zazwyczaj typu `object`nawet wtedy, gdy można stosować bardziej określonego typu.  
  
 **CZY ✓** nazwy zdarzeń klasy argumentu z sufiksem "EventArgs".  
  
## <a name="names-of-fields"></a>Nazwy pól  
 Wskazówki dotyczące nazewnictwa pól dotyczą pola statyczne publiczne i chronione. Wewnętrzne i prywatne pola nie są objęte wytyczne i pola publiczne lub chronione wystąpienie nie są dozwolone w [element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md).  
  
 **CZY ✓** Użyj PascalCasing w nazwach pól.  
  
 **CZY ✓** nazwać pola, przy użyciu rzeczownik, rzeczownik frazy lub przymiotnik.  
  
 **X nie** używać prefiksu dla nazw pól.  
  
 Na przykład nie umożliwia "g_" lub "s_" oznaczają pola statyczne.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
