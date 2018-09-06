---
title: Projekt pola
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65c54fe9a076a219c61280a98c390b16f56b5015
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43873945"
---
# <a name="field-design"></a>Projekt pola
Zasadą hermetyzacji jest jedną z najważniejszych koncepcje programowania obiektowego. Ta zasada mówi, dane przechowywane w ramach obiektu należy dostępny tylko dla tego obiektu.  
  
 Jest to przydatny sposób interpretowania zasady powiedzieć, że typem powinny zostać tak zaprojektowane, aby do pól typu (zmiany nazwy lub typu) zmian bez przerywania kodu innego niż dla elementów członkowskich typu. Interpretacja tego natychmiast oznacza, że wszystkie pola, muszą być w prywatnej.  
  
 Firma Microsoft Wyklucz stała i statycznego pola tylko do odczytu z to ścisłe ograniczenie, ponieważ takie pola prawie zgodnie z definicją, nigdy nie wymagana jest zmiana.  
  
 **X DO NOT** Podaj pól wystąpień, które są publiczne lub chronione.  
  
 Należy podać właściwości do uzyskiwania dostępu do pola, a nie nadawania publiczne lub chronione.  
  
 **✓ DO** Użyj stałych pól na stałe, które nigdy nie zmieni.  
  
 Kompilator spala wartości const pól bezpośrednio do wywoływania z kodu. W związku z tym wartości stałych nigdy nie można zmienić bez przerywania zgodność ryzyka.  
  
 **✓ DO** Użyj publiczne statyczne `readonly` pól dla wstępnie zdefiniowanych obiektów.  
  
 W przypadku wstępnie zdefiniowanych wystąpień tego typu je zadeklarować jako tylko do odczytu statyczne pola publiczne samego typu.  
  
 **X DO NOT** przypisać wystąpień typów modyfikowalną do `readonly` pola.  
  
 Typ zmienny to typ z wystąpieniami, które mogą być modyfikowane po ich są tworzone. Na przykład, tablice, większość kolekcji i strumienie są modyfikowalnych typów, ale <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, i <xref:System.String?displayProperty=nameWithType> są wszystkie niezmienne. Modyfikator tylko do odczytu w polu typu odwołania uniemożliwia wystąpienie przechowywane w polu od zastępowanego, ale nie uniemożliwia danych wystąpienia w polu przed modyfikacją, wywołując elementy zmiana wystąpienia programu.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)  
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
