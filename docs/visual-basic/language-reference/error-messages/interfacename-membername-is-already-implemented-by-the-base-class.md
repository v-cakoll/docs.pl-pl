---
title: '&#39;&lt;InterfaceName&gt;.&lt; membername&gt; &#39; został już zaimplementowany przez klasę bazową &#39; &lt;baseclassname&gt;&#39;. Ponowną implementację elementu &lt;typu&gt; zakłada, że'
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 22a3bd4e8c09c0d070e7fa5e75571a7215c3a274
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507203"
---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a>&#39;&lt;InterfaceName&gt;.&lt; membername&gt; &#39; został już zaimplementowany przez klasę bazową &#39; &lt;baseclassname&gt;&#39;. Ponowną implementację elementu &lt;typu&gt; zakłada, że
Właściwość, procedura lub zdarzenia w klasie pochodnej używa `Implements` klauzulę określania składowej interfejsu, który został już zaimplementowany w klasie bazowej.  
  
 Klasa pochodna może ponownie składowej interfejsu, który jest implementowany przez jej klasę bazową. Nie jest taka sama jak zastępowanie implementacji klasy podstawowej. Aby uzyskać więcej informacji, zobacz [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42015  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli planujesz ponownie składowej interfejsu, nie musisz podejmować żadnych działań. Kod w klasie pochodnej uzyskuje dostęp do składowej reimplemented chyba że używasz `MyBase` — słowo kluczowe do dostępu do implementacji klasy podstawowej.  
  
-   Jeśli nie zamierzasz ponownie składowej interfejsu, Usuń `Implements` klauzuli z deklaracji właściwość, procedura lub zdarzenie.  
  
## <a name="see-also"></a>Zobacz także
- [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
