---
title: 'Instrukcje: Sprawdzanie poprawności nazw plików oraz ścieżek w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: c0d39ecbaf9ca23c72e45b8839d268fbc38fe48e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648459"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Instrukcje: Sprawdzanie poprawności nazw plików oraz ścieżek w języku Visual Basic
W tym przykładzie zwraca `Boolean` wartość, która wskazuje, czy ciąg reprezentuje nazwę pliku lub ścieżkę. Sprawdzanie poprawności sprawdza, czy nazwa zawiera znaki, które nie są dozwolone przez system plików.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 W tym przykładzie nie sprawdza, czy nazwa niepoprawnie został umieszczony w dwukropki lub katalogi bez nazwy, czy długość nazwy przekracza maksymalną długość zdefiniowaną przez system. Ponadto nie sprawdza ona, czy aplikacja ma uprawnienia dostępu do zasobu systemu plików przy użyciu określonej nazwy.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Sprawdzanie poprawności ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
