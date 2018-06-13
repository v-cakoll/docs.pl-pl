---
title: 'Porady: sprawdzanie poprawności nazw plików oraz ścieżek w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: ab3df335bc5bba21d386bb69b12d840990e629fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647807"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Porady: sprawdzanie poprawności nazw plików oraz ścieżek w Visual Basic
W tym przykładzie zwraca `Boolean` wartość, która wskazuje, czy ciąg reprezentuje nazwę pliku lub ścieżkę. Sprawdzanie poprawności sprawdza, czy nazwa zawiera znaki, które nie są dozwolone w systemie plików.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 W tym przykładzie nie sprawdza, czy nazwa niepoprawnie umieścił dwukropki lub katalogów bez nazwy, czy długość nazwy przekracza maksymalną długość zdefiniowana w systemie. Go również nie sprawdza, czy aplikacja ma uprawnienie dostępu do zasobu systemu plików o określonej nazwie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.Path.GetInvalidPathChars%2A>  
 [Sprawdzanie poprawności ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
