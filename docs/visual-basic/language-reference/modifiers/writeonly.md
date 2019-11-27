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
ms.openlocfilehash: 847617ea6534089857a759fbea3bb16a3a5a36a1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344190"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Określa, że właściwość może być zapisywana, ale nie do odczytu.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="rules"></a>Reguły  
 **Kontekst deklaracji.** `WriteOnly` można używać tylko na poziomie modułu. Oznacza to, że kontekst deklaracji właściwości `WriteOnly` musi być klasą, strukturą lub modułem, i nie może być plikiem źródłowym, przestrzenią nazw ani procedurą.  
  
 Można zadeklarować właściwość jako `WriteOnly`, ale nie dla zmiennej.  
  
## <a name="when-to-use-writeonly"></a>Kiedy używać WriteOnly  
 Czasami kod zużywający ma mieć możliwość ustawienia wartości, ale nie Odkryj, co to jest. Na przykład dane poufne, takie jak numer rejestracji społecznościowej lub hasło, muszą być chronione przed dostępem przez dowolny składnik, który go nie ustawił. W takich przypadkach można użyć właściwości `WriteOnly`, aby ustawić wartość.  
  
> [!IMPORTANT]
> Podczas definiowania i używania właściwości `WriteOnly` należy wziąć pod uwagę następujące dodatkowe środki ochronne:  
  
- **Zastępuje.** Jeśli właściwość jest członkiem klasy, zezwól jej na wartość domyślną [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)i nie deklaruj jej `Overridable` ani `MustOverride`. Zapobiega to niepożądanemu dostępowi klasy pochodnej przez przesłonięcie.  
  
- **Poziom dostępu.** Jeśli przechowujesz poufne dane właściwości w co najmniej jednej zmiennej, zadeklaruj je jako [prywatne](../../../visual-basic/language-reference/modifiers/private.md) , aby żaden inny kod nie mógł uzyskać do nich dostępu.  
  
- **Szyfrowania.** Przechowuj wszystkie poufne dane w postaci zaszyfrowanej, a nie w postaci zwykłego tekstu. Jeśli złośliwy kod w jakiś sposób uzyskuje dostęp do tego obszaru pamięci, trudno jest wykorzystać dane. Szyfrowanie jest również przydatne, jeśli jest konieczne do serializacji poufnych danych.  
  
- **Resetowanie.** Gdy Klasa, struktura lub moduł definiujący właściwość jest przerywana, zresetuj dane poufne do wartości domyślnych lub innych wartości bez znaczenia. Zapewnia to dodatkową ochronę, gdy ten obszar pamięci jest bezpłatny do uzyskania dostępu ogólnego.  
  
- **Trwałość.** Nie Utrwalaj poufnych danych, na przykład na dysku, jeśli można je uniknąć. Ponadto nie należy zapisywać poufnych danych w Schowku.  
  
 Modyfikator `WriteOnly` może być używany w tym kontekście:  
  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
