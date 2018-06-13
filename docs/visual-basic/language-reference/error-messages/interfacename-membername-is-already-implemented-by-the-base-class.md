---
title: '&#39;&lt;InterfaceName&gt;.&lt; membername&gt; &#39; został już zaimplementowany przez klasę podstawową &#39; &lt;baseclassname&gt;&#39;. Ponowną implementację elementu &lt;typu&gt; założono, że'
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 9054c293ede9db4637f23579407f2f76db29f2ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588973"
---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a>&#39;&lt;InterfaceName&gt;.&lt; membername&gt; &#39; został już zaimplementowany przez klasę podstawową &#39; &lt;baseclassname&gt;&#39;. Ponowną implementację elementu &lt;typu&gt; założono, że
Właściwość, procedura lub zdarzenia w klasie pochodnej używa `Implements` klauzuli Określanie elementu członkowskiego interfejsu, który jest już zaimplementowana w klasie podstawowej.  
  
 Klasa pochodna może reimplement elementu członkowskiego interfejsu, który jest implementowany przez jej klasa podstawowa. Nie jest taka sama jak zastępowanie implementacji klasy podstawowej. Aby uzyskać więcej informacji, zobacz [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
 Domyślnie ten komunikat jest ostrzeżenie. Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42015  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli zamierzasz reimplement elementu członkowskiego interfejsu, nie trzeba podejmować żadnych działań. Kod w klasie pochodnej uzyskuje dostęp do elementu członkowskiego reimplemented tylko w przypadku `MyBase` — słowo kluczowe do implementacji klasy podstawowej.  
  
-   Jeśli nie zamierzasz reimplement elementu członkowskiego interfejsu, Usuń `Implements` klauzuli z deklaracji właściwości, procedura lub zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
