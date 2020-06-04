---
title: 'Instrukcje: Sprawdzanie poprawności nazw plików oraz ścieżek'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: 3b4695dfbcaf05c73bd53af5be7a49d081eb8e47
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410583"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Porady: sprawdzanie poprawności nazw plików oraz ścieżek w Visual Basic
Ten przykład zwraca `Boolean` wartość wskazującą, czy ciąg reprezentuje nazwę pliku lub ścieżkę. Sprawdzanie poprawności sprawdza, czy nazwa zawiera znaki, które nie są dozwolone przez system plików.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 Ten przykład nie sprawdza, czy nazwa ma nieprawidłowo umieszczone kolonie lub katalogi bez nazwy lub jeśli długość nazwy przekracza maksymalną długość zdefiniowaną przez system. Nie sprawdza także, czy aplikacja ma uprawnienia dostępu do zasobu systemu plików o określonej nazwie.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Sprawdzanie poprawności ciągów w Visual Basic](validating-strings.md)
