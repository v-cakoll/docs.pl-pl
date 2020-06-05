---
title: WriteOnly
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: a9fa0a3a23561215d6ff122bc8e609b68ca6fc30
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386637"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Określa, że właściwość może być zapisywana, ale nie do odczytu.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="rules"></a>Reguły  
 **Kontekst deklaracji.** Można używać `WriteOnly` tylko na poziomie modułu. Oznacza to, że kontekst deklaracji `WriteOnly` właściwości musi być klasą, strukturą lub modułem, i nie może być plikiem źródłowym, przestrzenią nazw ani procedurą.  
  
 Właściwość można zadeklarować jako `WriteOnly` , ale nie zmienną.  
  
## <a name="when-to-use-writeonly"></a>Kiedy używać WriteOnly  
 Czasami kod zużywający ma mieć możliwość ustawienia wartości, ale nie Odkryj, co to jest. Na przykład dane poufne, takie jak numer rejestracji społecznościowej lub hasło, muszą być chronione przed dostępem przez dowolny składnik, który go nie ustawił. W takich przypadkach można użyć `WriteOnly` właściwości, aby ustawić wartość.  
  
> [!IMPORTANT]
> Podczas definiowania i używania właściwości należy `WriteOnly` wziąć pod uwagę następujące dodatkowe środki ochronne:  
  
- **Zastępuje.** Jeśli właściwość jest członkiem klasy, zezwól jej na wartość domyślną [NotOverridable](notoverridable.md)i nie deklaruj `Overridable` ani `MustOverride` . Zapobiega to niepożądanemu dostępowi klasy pochodnej przez przesłonięcie.  
  
- **Poziom dostępu.** Jeśli przechowujesz poufne dane właściwości w co najmniej jednej zmiennej, zadeklaruj je jako [prywatne](private.md) , aby żaden inny kod nie mógł uzyskać do nich dostępu.  
  
- **Szyfrowania.** Przechowuj wszystkie poufne dane w postaci zaszyfrowanej, a nie w postaci zwykłego tekstu. Jeśli złośliwy kod w jakiś sposób uzyskuje dostęp do tego obszaru pamięci, trudno jest wykorzystać dane. Szyfrowanie jest również przydatne, jeśli jest konieczne do serializacji poufnych danych.  
  
- **Resetowanie.** Gdy Klasa, struktura lub moduł definiujący właściwość jest przerywana, zresetuj dane poufne do wartości domyślnych lub innych wartości bez znaczenia. Zapewnia to dodatkową ochronę, gdy ten obszar pamięci jest bezpłatny do uzyskania dostępu ogólnego.  
  
- **Trwałość.** Nie Utrwalaj poufnych danych, na przykład na dysku, jeśli można je uniknąć. Ponadto nie należy zapisywać poufnych danych w Schowku.  
  
 `WriteOnly`Modyfikator może być używany w tym kontekście:  
  
 [Property — Instrukcja](../statements/property-statement.md)  
  
## <a name="see-also"></a>Zobacz też

- [Trybie](readonly.md)
- [Użytek](private.md)
- [Słowa kluczowe](../keywords/index.md)
