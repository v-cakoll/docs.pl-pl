---
title: WriteOnly (Visual Basic)
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
ms.openlocfilehash: 4f34f7f4ada3f8d61c9d855eab1b8b073a3d5ed8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599206"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Określa, że właściwości mogą być zapisane, ale nie do odczytu.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="rules"></a>Reguły  
 **Kontekst deklaracji.** Można użyć `WriteOnly` tylko na poziomie modułu. Oznacza to, że w kontekście deklaracji `WriteOnly` właściwość musi być klasą, strukturą lub modułu i nie może być plik źródłowy, przestrzeni nazw lub procedury.  
  
 Można zadeklarować właściwości jako `WriteOnly`, ale nie zmiennej.  
  
## <a name="when-to-use-writeonly"></a>Kiedy należy używać WriteOnly  
 Czasami ma odbierającą kod, aby można było ustawić wartość, ale nie odnajdzie co to jest. Na przykład poufnych danych, takich jak numer rejestracji społecznościowych lub hasło, musi być chronione przed dostępem przez każdego składnika, który nie ustawiony. W takich przypadkach można użyć `WriteOnly` właściwości można ustawić wartości.  
  
> [!IMPORTANT]
>  Po zdefiniowaniu i użyj `WriteOnly` właściwość, należy wziąć pod uwagę następujące dodatkowe środki zabezpieczające:  
  
-   **Zastępowanie.** Jeśli właściwość jest elementem członkowskim klasy, zezwolenie na domyślnie [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), a nie deklaruj `Overridable` lub `MustOverride`. Zapobiega to wprowadzania niepożądanych dostępu za pomocą zastąpienia klasy pochodnej.  
  
-   **Poziom dostępu.** Właściwości poufne dane są przechowywane w jedną lub więcej zmiennych, zadeklarować je [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) tak, aby żadnego innego kodu można uzyskiwać do nich dostęp.  
  
-   **Szyfrowanie.** Przechowywane są wszystkie poufne dane w postaci zaszyfrowanej, a nie w postaci zwykłego tekstu. Jeśli złośliwy kod w jakiś sposób uzyska dostęp do tego obszaru pamięci, jest trudniej należy użyć danych. Szyfrowanie jest również przydatne, jeśli jest konieczne do serializowania danych poufnych.  
  
-   **Resetowanie.** Klasy, struktury lub modułu definiowania właściwość zostało zakończone, zresetowanie poufne dane do wartości domyślnych lub inne wartości znaczenia. Daje to dodatkowej ochrony, gdy ten obszar pamięci zostanie zwolniona ogólne dostępu.  
  
-   **Trwałość.** Nie są zachowywane poufnych danych, na przykład na dysku, jeśli można go uniknąć. Ponadto nie zapisuj żadnych poufnych danych do Schowka.  
  
 `WriteOnly` Modyfikatora można używać w tym kontekście:  
  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
