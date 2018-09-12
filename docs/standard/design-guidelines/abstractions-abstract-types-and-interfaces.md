---
title: Abstrakcje (typy abstrakcyjne i interfejsy)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ad8b2dd3dbf2a7a75c98a3115d4351dfea4e1a0
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44698367"
---
# <a name="abstractions-abstract-types-and-interfaces"></a>Abstrakcje (typy abstrakcyjne i interfejsy)
Abstrakcja to typ, który zawiera opis kontraktu, ale nie zapewnia pełnej implementacji kontraktu. Abstrakcje są zwykle implementowane jako abstrakcyjnych klas lub interfejsów, a pochodzą one z dobrze zdefiniowanego zestawu dokumentacji opisujące wymagany semantykę typów Implementowanie kontraktu. Najważniejsze elementy abstrakcji w programie .NET Framework między innymi <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, i <xref:System.Object>.  
  
 Możesz rozszerzyć struktury przez implementację typu konkretnego, który obsługuje kontrakt abstrakcję i przy użyciu tego konkretnego typu przy użyciu framework API odbierająca komunikaty (działającej na) pozyskiwania.  
  
 Zrozumiałe i przydatne abstrakcji, będącego wytrzymać test czasu jest bardzo trudne do projektowania. Trudności w głównym niedługo właściwy zestaw elementów członkowskich, nie ma więcej i nie mniejszej liczby. Jeśli klasą abstrakcyjną ma zbyt wiele elementów członkowskich, staje się trudne lub niemożliwe nawet do zaimplementowania. Ma za mało elementów członkowskich dla funkcji uzgodnionego, staje się bezużyteczny w wielu scenariuszach interesujące.  
  
 Zbyt wiele abstrakcje w ramach negatywny wpływ na użyteczność Framework. Często jest dosyć trudno jest zrozumieć abstrakcję bez zrozumienia, jak pasuje do większy obraz konkretnych implementacji i interfejsy API działające pozyskiwania. Nazwy abstrakcje i ich elementów członkowskich są także musi być abstrakcyjna, co często sprawia, że ich tajemnicze i unapproachable bez pierwszy zrozumienia szersze kontekstu ich użycia.  
  
 Jednak abstrakcje rozszerzalność wyjątkowo zaawansowana, często nie pasują do innych mechanizmów rozszerzalności. Są one w samym sercu wielu wzorców architektury, takich jak dodatki plug-in, Inwersja kontroli (IoC), potoki i tak dalej. Są one również bardzo ważne w przypadku testowania struktur. Abstrakcji dobrej należy możliwość tworzenia wycinków się dużymi zależności na potrzeby testowania jednostek. Podsumowując abstrakcje są odpowiedzialne za sought-after bogactwa nowoczesnych platform zorientowane obiektowo.  
  
 **X DO NOT** Podaj obiektów abstrakcyjnych, chyba że są one przetestowane przez kilka konkretnych implementacji i interfejsów API korzystających z obiekty abstrakcyjne.  
  
 **✓ DO** dokładnie wybór między klasą abstrakcyjną i interfejs podczas projektowania abstrakcję.  
  
 **✓ CONSIDER** podając odwołanie testy konkretnych implementacji obiektów abstrakcyjnych. Testy te należy umożliwić użytkownikom sprawdzić, czy ich implementacji prawidłowo zaimplementować kontrakt.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
- [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
