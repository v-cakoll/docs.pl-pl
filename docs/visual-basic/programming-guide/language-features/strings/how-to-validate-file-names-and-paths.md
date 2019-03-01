---
title: 'Instrukcje: Sprawdzanie poprawności nazw plików oraz ścieżek w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: d29553071d68319d754406b3104da6e096f908fd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975527"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Instrukcje: Sprawdzanie poprawności nazw plików oraz ścieżek w języku Visual Basic
W tym przykładzie zwraca `Boolean` wartość, która wskazuje, czy ciąg reprezentuje nazwę pliku lub ścieżkę. Sprawdzanie poprawności sprawdza, czy nazwa zawiera znaki, które nie są dozwolone przez system plików.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 W tym przykładzie nie sprawdza, czy nazwa niepoprawnie został umieszczony w dwukropki lub katalogi bez nazwy, czy długość nazwy przekracza maksymalną długość zdefiniowaną przez system. Ponadto nie sprawdza ona, czy aplikacja ma uprawnienia dostępu do zasobu systemu plików przy użyciu określonej nazwy.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Sprawdzanie poprawności ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
