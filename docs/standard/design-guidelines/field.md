---
title: Pole projektu
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d47934c3fed17f75a97ef5da0397c6ceba53d68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="field-design"></a>Pole projektu
Zasada hermetyzacji jest jednym z najważniejsze koncepcje zorientowane obiektowo projektu. Ta zasada mówi, że dane przechowywane wewnątrz obiektu powinien być dostępny tylko dla tego obiektu.  
  
 Jest wygodny sposób, aby zinterpretować zasady oznacza, że typ należy tak zaprojektować, dzięki czemu można wprowadzać zmiany do pól typu (zmiany nazwy lub typu) bez przerywania kodu innego niż dla elementów członkowskich tego typu. Niniejsza interpretacja natychmiast oznacza, że wszystkie pola muszą być prywatne.  
  
 Wyłączamy stałej i statycznego pola tylko do odczytu z tego ograniczenia strict, ponieważ takie pola prawie zgodnie z definicją nigdy nie wymaga zmiany.  
  
 **X nie** Podaj pól wystąpień, które są publiczne lub chronione.  
  
 Należy podać właściwości do uzyskiwania dostępu do pola zamiast nadawania publiczne lub chronione.  
  
 **CZY ✓** Użyj stałych pól na stałe, które nigdy nie zmieni.  
  
 Kompilator pali wartości pól const bezpośrednio do wywoływania z kodu. W związku z tym wartości stałych nigdy nie można zmienić bez ryzyka fundamentalne zgodności.  
  
 **CZY ✓** Użyj publiczne statyczne `readonly` pól dla wstępnie zdefiniowanych obiektów.  
  
 W przypadku wystąpienia wstępnie zdefiniowanego typu zadeklarować je jako publiczną pola statycznego tylko do odczytu tego samego typu.  
  
 **X nie** przypisać wystąpień typów modyfikowalną do `readonly` pola.  
  
 Modyfikowalne typ jest typem z wystąpieniami, które można zmodyfikować po utrzymującego. Na przykład tablic, większość kolekcji i strumienie są modyfikowalne typów, ale <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, i <xref:System.String?displayProperty=nameWithType> są niezmienne wszystkie. Wystąpienie przechowywana w polu od zastępowanego uniemożliwia modyfikatora tylko do odczytu w polu typu odwołania, ale nie zapobiega danych wystąpienia w polu przed modyfikacją przez wywołanie członków zmiana wystąpienia programu.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
