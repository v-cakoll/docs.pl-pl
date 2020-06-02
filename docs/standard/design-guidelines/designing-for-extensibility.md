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
ms.openlocfilehash: 406c15b6ce42b637ed1bbb61761d05e040995579
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280247"
---
# <a name="designing-for-extensibility"></a>Projektowanie pod kątem rozszerzalności
Jednym z ważniejszych aspektów projektowania struktury jest upewnienie się, że rozszerzalność struktury jest starannie rozpatrywana. Wymaga to zrozumienia kosztów i korzyści związanych z różnymi mechanizmami rozszerzalności. Ten rozdział ułatwia podjęcie decyzji, które mechanizmy rozszerzalności — podklasy, zdarzenia, wirtualne elementy członkowskie, wywołania zwrotne i tak dalej — mogą najlepiej spełniać wymagania platformy.  
  
 Istnieje wiele sposobów na umożliwienie rozszerzalności w strukturach. Są one większe niż tańsze, ale tańsze, ale kosztowne. W przypadku danego wymagania dotyczącego rozszerzalności należy wybrać najniższy, kosztowny mechanizm rozszerzania spełniający wymagania. Należy pamiętać, że jest zwykle możliwe dodanie większej liczby rozszerzeń później, ale nigdy nie należy wprowadzać zmian.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Niezapieczętowane klasy](unsealed-classes.md)  
 [Chronione elementy członkowskie](protected-members.md)  
 [Zdarzenia i wywołania zwrotne](events-and-callbacks.md)  
 [Wirtualne elementy członkowskie](virtual-members.md)  
 [Abstrakcje (Typy abstrakcyjne i interfejsy)](abstractions-abstract-types-and-interfaces.md)  
 [Klasy podstawowe do implementowania streszczeń](base-classes-for-implementing-abstractions.md)  
 [Pieczętowanie](sealing.md)  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania struktury](index.md)
