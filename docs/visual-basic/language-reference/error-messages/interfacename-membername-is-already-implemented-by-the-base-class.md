---
title: "'<interfacename>. <membername>'został już zaimplementowany przez klasę bazową'<baseclassname>'. Ponowną implementację elementu <type> zakłada, że"
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 5943eff5fa7e68da9905e3e589eea264c06943c1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593314"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a>'\<interfacename >. \<membername > 'został już zaimplementowany przez klasę bazową\<baseclassname >'. Ponowną implementację elementu \<typ > zakłada, że
Właściwość, procedura lub zdarzenia w klasie pochodnej używa `Implements` klauzulę określania składowej interfejsu, który został już zaimplementowany w klasie bazowej.  
  
 Klasa pochodna może ponownie składowej interfejsu, który jest implementowany przez jej klasę bazową. Nie jest taka sama jak zastępowanie implementacji klasy podstawowej. Aby uzyskać więcej informacji, zobacz [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42015  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli planujesz ponownie składowej interfejsu, nie musisz podejmować żadnych działań. Kod w klasie pochodnej uzyskuje dostęp do składowej reimplemented chyba że używasz `MyBase` — słowo kluczowe do dostępu do implementacji klasy podstawowej.  
  
- Jeśli nie zamierzasz ponownie składowej interfejsu, Usuń `Implements` klauzuli z deklaracji właściwość, procedura lub zdarzenie.  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
