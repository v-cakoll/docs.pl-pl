---
title: Obiekty abstrakcyjne (typy abstrakcyjne i interfejsy)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 276c5883487d8fba47d7fb80060d4c947e0f6cd6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="abstractions-abstract-types-and-interfaces"></a>Obiekty abstrakcyjne (typy abstrakcyjne i interfejsy)
Abstrakcja jest typem, który opisuje kontrakt, ale nie zapewnia pełnej implementacji kontraktu. Obiekty abstrakcyjne są zazwyczaj zaimplementowane jako interfejsów lub klas abstrakcyjnych i pochodzą z dobrze zdefiniowany zestaw dokumentacji opisujące wymagany semantyka typów Implementowanie kontraktu. Poniżej wymieniono niektóre z najważniejszych abstrakcje w programie .NET Framework <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, i <xref:System.Object>.  
  
 Struktury można rozszerzyć, implementując konkretnego typu, który obsługuje kontrakt abstrakcję i przy użyciu tego konkretnego typu z framework interfejsów API odbierającą (działającej na) pozyskiwania.  
  
 Znaczenie i przydatne abstrakcji, będącą wytrzymać test czasu jest bardzo trudne do projektowania. Główne trudności otrzymuje prawidłowego zestawu elementów członkowskich, ma więcej i nie mniej. Jeśli abstrakcję ma zbyt wiele elementów członkowskich, staje się trudne lub niemożliwe nawet do zaimplementowania. Jeśli ma za mało elementów członkowskich uzgodnionej funkcji, staje się on bezużyteczny w wielu scenariuszach interesujące.  
  
 Zbyt wiele obiektów abstrakcyjnych w ramach negatywny wpływ na użyteczność platformy. Często jest to bardzo trudne do zrozumienia abstrakcję bez zrozumienia, jak mieścił się w większych obraz konkretnych implementacji i działających na pozyskiwania interfejsy API. Nazwy obiektów abstrakcyjnych i ich elementy członkowskie są także niekoniecznie abstrakcyjnego, który często sprawia, że ich one niezrozumiałe i unapproachable bez zrozumienia pierwszy szerszym kontekstem ich użycia.  
  
 Jednak abstrakcje rozszerzalność niezwykle wydajnych innych mechanizmów rozszerzalności często nie pasuje. Są one fundament wiele architektury wzorców, takich jak dodatki plug-in, Inwersja kontroli (IoC), potoki i tak dalej. Są one również bardzo ważne dla pola struktury. Dobrym abstrakcje umożliwiają stub limit duże zależności na potrzeby testowania jednostek. Podsumowując obiekty abstrakcyjne są odpowiedzialne za sought-after formatem nowoczesny zorientowany obiektowo struktury.  
  
 **X nie** Podaj obiektów abstrakcyjnych, chyba że są one przetestowane przez kilka konkretnych implementacji i interfejsów API korzystających z obiekty abstrakcyjne.  
  
 **CZY ✓** dokładnie wybór między klasą abstrakcyjną i interfejs podczas projektowania abstrakcję.  
  
 **ROZWAŻ ✓** podając odwołanie testy konkretnych implementacji obiektów abstrakcyjnych. Testy te należy umożliwić użytkownikom sprawdzić, czy ich implementacji prawidłowo zaimplementować kontrakt.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
