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
ms.openlocfilehash: 1b8de27e872914ba59d73126d2a9a7c42609165e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58829032"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Określa, że właściwości mogą być zapisywane, ale nie do odczytu.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="rules"></a>reguły  
 **Kontekst deklaracji.** Możesz użyć `WriteOnly` tylko na poziomie modułu. Oznacza to, że kontekst deklaracji `WriteOnly` właściwość musi być klasy, struktury lub modułu i nie może być plikiem źródłowym, przestrzeń nazw lub procedury.  
  
 Można zadeklarować właściwości jako `WriteOnly`, ale nie zmienną.  
  
## <a name="when-to-use-writeonly"></a>Kiedy należy używać WriteOnly  
 Czasami kod konsumencki, aby można było ustawić wartość, ale nie zobaczyć, jakie go. Na przykład dane poufne, takie jak numer rejestracji społecznościowych lub hasła, muszą być chronione przed dostępem przez dowolny składnik, który nie ustawiony. W takich przypadkach można użyć `WriteOnly` właściwość można ustawić wartości.  
  
> [!IMPORTANT]
>  Podczas definiowania i stosowania `WriteOnly` właściwość, należy wziąć pod uwagę następujące dodatkowe środki zabezpieczające:  
  
-   **Zastępowanie.** Jeśli właściwość jest składową klasy, zezwalała na domyślnie [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), a nie deklaruj `Overridable` lub `MustOverride`. Uniemożliwia to wprowadzanie niepożądany dostęp za pomocą zastąpienia przez klasę pochodną.  
  
-   **Poziom dostępu.** Jeśli przytrzymasz właściwości poufnych danych w jednej lub więcej zmiennych je zadeklarować [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) tak, aby żadnego innego kodu można uzyskiwać do nich dostęp.  
  
-   **Encryption.** Store wszystkie poufne dane w postaci zaszyfrowanej, a nie w postaci zwykłego tekstu. Jeśli złośliwy kod w jakiś sposób uzyskuje dostęp do tego obszaru pamięci, jest trudniejsze użyć danych. Szyfrowanie jest również przydatne, jeśli to konieczne do serializowania danych poufnych.  
  
-   **Resetowanie.** Klasy, struktury lub modułu definiowania właściwość zostanie przerwany, zresetowanie danych poufnych do wartości domyślnych lub inne wartości bez znaczenia. Zapewnia dodatkową ochronę, gdy ten obszar pamięci jest zwalniana dla ogólnego dostępu.  
  
-   **Trwałość.** Nie są zachowywane poufnych danych, na przykład na dysku, jeśli można go uniknąć. Ponadto nie wpisuj poufnych danych do Schowka.  
  
 `WriteOnly` Modyfikatora można używać w tym kontekście:  
  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
