---
title: '&lt;komunikat&gt; tego błędu może być również spowodowane połączenie odwołania pliku z odwołaniem projektu do zestawu &#39; &lt;assemblyname&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 498ca74497077e3268aa8cb25ce5121f3c9ea59d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588340"
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a>&lt;komunikat&gt; tego błędu może być również spowodowane połączenie odwołania pliku z odwołaniem projektu do zestawu &#39; &lt;assemblyname&gt;&#39;
\<komunikat > tego błędu może być również spowodowane połączenie odwołania pliku z odwołaniem projektu do zestawu "\<assemblyname >. W takim przypadku spróbuj zamienić odwołanie pliku do "\<assemblyfilename >" w projekcie "\<projectname1 >" na odwołanie projektu do "\<projectname2 >".  
  
 Członkiem innego projektu uzyskuje dostęp do kodu w projekcie, ale konfiguracja rozwiązania nie zezwala na kompilator Visual Basic rozpoznać odwołania.  
  
 Dostęp do typu zdefiniowanego w innym zestawie, kompilator Visual Basic musi mieć odwołanie do tego zestawu. Musi to być pojedynczą, jednoznaczne odwołanie, które nie powoduje cykliczne odwołania między projektami.  
  
 **Identyfikator błędu:** BC30971  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Określ, który projekt tworzy najlepsze zestawu dla projektu do odwołania. Do tej decyzji można użyć kryteriów, takich jak łatwość dostępu do plików i częstotliwość aktualizacji.  
  
2.  We właściwościach projektu Dodaj odwołanie do projektu, który zawiera zestaw, który definiuje typ, którego używasz.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)  
 [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)  
 [Rozwiązywanie problemów z przerwanymi odwołaniami](/visualstudio/ide/troubleshooting-broken-references)
