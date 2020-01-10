---
title: Projektowanie pod kątem rozszerzalności
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: cd5db2d1e299df1b3d0f706ebc507e6855b72505
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709468"
---
# <a name="designing-for-extensibility"></a>Projektowanie pod kątem rozszerzalności
Jednym z ważniejszych aspektów projektowania struktury jest upewnienie się, że rozszerzalność struktury jest starannie rozpatrywana. Wymaga to zrozumienia kosztów i korzyści związanych z różnymi mechanizmami rozszerzalności. Ten rozdział ułatwia podjęcie decyzji, które mechanizmy rozszerzalności — podklasy, zdarzenia, wirtualne elementy członkowskie, wywołania zwrotne i tak dalej — mogą najlepiej spełniać wymagania platformy.  
  
 Istnieje wiele sposobów na umożliwienie rozszerzalności w strukturach. Są one większe niż tańsze, ale tańsze, ale kosztowne. W przypadku danego wymagania dotyczącego rozszerzalności należy wybrać najniższy, kosztowny mechanizm rozszerzania spełniający wymagania. Należy pamiętać, że jest zwykle możliwe dodanie większej liczby rozszerzeń później, ale nigdy nie należy wprowadzać zmian.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Niezapieczętowane klasy](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [Chronione elementy członkowskie](../../../docs/standard/design-guidelines/protected-members.md)  
 [Zdarzenia i wywołania zwrotne](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [Wirtualne elementy członkowskie](../../../docs/standard/design-guidelines/virtual-members.md)  
 [Abstrakcje (typy abstrakcyjne i interfejsy)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [Klasy bazowe na potrzeby implementowania abstrakcji](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [Pieczętowanie](../../../docs/standard/design-guidelines/sealing.md)  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
