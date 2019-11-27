---
title: 'Instrukcje: sprawdzanie poprawności nazw plików i ścieżek'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: cc4d275d469860aa19c45ca0fe0401b709b42d82
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344369"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a>Porady: sprawdzanie poprawności nazw plików oraz ścieżek w Visual Basic
Ten przykład zwraca wartość `Boolean`, która wskazuje, czy ciąg reprezentuje nazwę pliku lub ścieżkę. Sprawdzanie poprawności sprawdza, czy nazwa zawiera znaki, które nie są dozwolone przez system plików.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 Ten przykład nie sprawdza, czy nazwa ma nieprawidłowo umieszczone kolonie lub katalogi bez nazwy lub jeśli długość nazwy przekracza maksymalną długość zdefiniowaną przez system. Nie sprawdza także, czy aplikacja ma uprawnienia dostępu do zasobu systemu plików o określonej nazwie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [Sprawdzanie poprawności ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
