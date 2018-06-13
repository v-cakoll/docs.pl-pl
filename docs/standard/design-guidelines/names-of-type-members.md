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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575352"
---
# <a name="names-of-type-members"></a>Nazwy elementów członkowskich typu
Typy składają się z elementów członkowskich: metody, właściwości, zdarzenia, konstruktorów i pól. W poniższych sekcjach opisano zasady nazewnictwa elementy członkowskie typu.  
  
## <a name="names-of-methods"></a>Nazwy metod  
 Ponieważ metody służą do podjęcia działań, zaleceń dotyczących projektowania wymagają nazwy metod zleceń ani fraz zlecenia. Również po ta wytyczna służy do odróżnienia nazwy metod nazw właściwości i typów, które są rzeczownik lub przymiotnik fraz.  
  
 **CZY ✓** Nadaj nazwy metody, które mogą lub zlecenie fraz.  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a>Nazwy właściwości  
 W przeciwieństwie do innych członków właściwości powinny mieć nazwy przymiotników lub frazę rzeczownik. Wynika to z właściwością odnosi się do danych i odzwierciedla nazwę właściwości, która. PascalCasing zawsze jest używany dla nazwy właściwości.  
  
 **CZY ✓** nazwy właściwości za pomocą rzeczownik, rzeczownik frazy lub przymiotnik.  
  
 **X nie** właściwości pasujących do nazwy metody "Get", jak w poniższym przykładzie:  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 Ten wzorzec zazwyczaj wskazuje, że właściwość naprawdę powinna być metody.  
  
 **CZY ✓** nazwy właściwości kolekcji o liczbie mnogiej frazy opisujące elementów w kolekcji zamiast za pomocą pojedynczej frazy "List" lub "Collection".  
  
 **CZY ✓** nazwę logiczną właściwości frazą potwierdzającego (`CanSeek` zamiast `CantSeek`). Opcjonalnie można również prefiksu logiczną właściwości z "Is", "można" lub "Ma," tylko wtedy, gdy dodaje wartość.  
  
 **ROZWAŻ ✓** nadanie właściwości taką samą nazwę jak jego typu.  
  
 Na przykład następująca właściwość poprawnie pobiera i ustawia wartość wyliczenia o nazwie `Color`, więc nosi nazwę właściwości `Color`:  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a>Nazwy zdarzenia  
 Zdarzenia zawsze odwołuje się do niektórych działań, albo jest w toku lub, który wystąpił. W związku z tym tak jak w przypadku metod, zdarzenia są nazywane zleceń, a czas zlecenie jest używany do określania czasu, gdy zdarzenie zostanie wywołane.  
  
 **CZY ✓** Nazwa zdarzenia z zlecenie lub zlecenia wyrażenia.  
  
 Przykłady obejmują `Clicked`, `Painting`, `DroppedDown`i tak dalej.  
  
 **CZY ✓** nadać nazwy zdarzenia z koncepcji przed i po, przy użyciu obecny i użycie czasów w przeszłości.  
  
 Na przykład, czy można wywołać zamknięcia zdarzenie, które jest wywoływane przed zamknięciem okna `Closing`, i czy można wywołać, który jest uruchamiany po zamknięciu okna `Closed`.  
  
 **X nie** Użyj "Przed" lub "Po" prefiksy lub postfixes, aby wskazać przed i po zdarzenia. Użyj obecne i użycie czasów przeszłości zgodnie z opisem tylko.  
  
 **CZY ✓** Nazwa procedury obsługi zdarzeń (obiekty delegowane używane jako typy zdarzeń) wraz z sufiksem "EventHandler", jak pokazano w poniższym przykładzie:  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 **CZY ✓** dwa parametry o nazwie `sender` i `e` w obsłudze zdarzeń.  
  
 Parametr nadawcy reprezentuje obiekt, który wywołał zdarzenie. Parametr nadawcy jest zwykle typu `object`nawet wtedy, gdy można zastosować bardziej określonego typu.  
  
 **CZY ✓** Nazwa zdarzenia klasy argument wraz z sufiksem "EventArgs".  
  
## <a name="names-of-fields"></a>Nazwy pól  
 Wskazówki dotyczące nazewnictwa pola dotyczą pola statyczne publiczne i chronione. Pola wewnętrzne i prywatne nie są objęte wytycznych i pól wystąpień publiczne lub chronione nie są dozwolone w [zaleceń dotyczących projektowania elementu członkowskiego](../../../docs/standard/design-guidelines/member.md).  
  
 **CZY ✓** Użyj PascalCasing w nazwach pól.  
  
 **CZY ✓** nazwy pól przy użyciu rzeczownik, rzeczownik frazy lub przymiotnik.  
  
 **X nie** użyć prefiksu nazwy pól.  
  
 Na przykład nie umożliwia "g_" lub "s_" wskazują pola statyczne.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
