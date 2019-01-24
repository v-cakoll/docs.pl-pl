---
title: '&lt;komunikat&gt; tego błędu może być również ze względu na połączenie odwołania pliku z odwołaniem projektu do zestawu &#39; &lt;assemblyname&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: d4fb2a8985a21ecea5056b83d2766e8dc468180d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528995"
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a>&lt;komunikat&gt; tego błędu może być również ze względu na połączenie odwołania pliku z odwołaniem projektu do zestawu &#39; &lt;assemblyname&gt;&#39;
\<komunikat > tego błędu może być również ze względu na połączenie odwołania pliku z odwołaniem projektu do zestawu "\<nazwa_zestawu >. W takim przypadku spróbuj wymienić odwołanie pliku do "\<assemblyfilename >' w projekcie"\<projectname1 > "z odwołaniem projektu do"\<projectname2 > ".  
  
 Kod w projekcie uzyskuje dostęp do składową innego projektu, ale konfiguracji rozwiązania nie zezwala na kompilator języka Visual Basic, aby rozpoznać odwołania.  
  
 Aby uzyskać dostęp do typu zdefiniowanego w innym zestawie, kompilator Visual Basic musi mieć odwołania do tego zestawu. Musi to być odwołanie pojedynczego, jednoznaczną nie powoduje odwołania cykliczne między projektami.  
  
 **Identyfikator błędu:** BC30971  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Ustal, który projekt daje najlepsze zestawu dla Twojego projektu do odwołania. Ta decyzja można skorzystać z kryteriów, takich jak łatwość dostępu do plików i częstotliwość aktualizacji.  
  
2.  We właściwościach projektu Dodaj odwołanie do projektu, który zawiera zestaw, który definiuje typ, którego używasz.  
  
## <a name="see-also"></a>Zobacz także
- [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)
- [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
- [Rozwiązywanie problemów z przerwanymi odwołaniami](/visualstudio/ide/troubleshooting-broken-references)
