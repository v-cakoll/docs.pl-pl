---
title: Zmienna „<variablename>” jest używana, zanim zostanie do niej przypisana wartość
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: 34718243172d3b1a238a813268e672d62c4eeb6c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406537"
---
# <a name="variable-variablename-is-used-before-it-has-been-assigned-a-value"></a>Zmienna „\<variablename>” jest używana, zanim zostanie do niej przypisana wartość
Zmienna " \<variablename> " jest używana przed przypisaniem do niej wartości. Wyjątek odwołania o wartości null może wynikać w czasie wykonywania.  
  
 Aplikacja ma co najmniej jedną możliwą ścieżkę za pomocą kodu, który odczytuje zmienną przed przypisaniem do niej żadnej wartości.  
  
 Jeśli zmienna nie ma przypisanej wartości, ma wartość domyślną dla tego typu danych. Dla typu danych referencyjnych wartość domyślna to [Nothing](../nothing.md). Odczytywanie zmiennej odniesienia, która ma wartość, `Nothing` może spowodować wystąpienie <xref:System.NullReferenceException> w pewnych okolicznościach.  
  
 Domyślnie ten komunikat jest ostrzeżeniem. Aby uzyskać więcej informacji na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42104  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Sprawdź logikę przepływu sterowania i upewnij się, że zmienna ma prawidłową wartość przed przekazaniem kontroli do dowolnej instrukcji, która odczytuje ją.  
  
- Jednym ze sposobów zagwarantowania, że zmienna zawsze ma prawidłową wartość, jest zainicjowanie jej jako części swojej deklaracji. Zobacz "Inicjalizacja" w [instrukcji Dim](../statements/dim-statement.md).  
  
## <a name="see-also"></a>Zobacz też

- [Dim, instrukcja](../statements/dim-statement.md)
- [Deklaracja zmiennej](../../programming-guide/language-features/variables/variable-declaration.md)
- [Rozwiązywanie problemów związanych ze zmiennymi](../../programming-guide/language-features/variables/troubleshooting-variables.md)
