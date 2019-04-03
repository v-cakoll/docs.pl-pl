---
title: <message> Ten błąd może również być spowodowany połączenie odwołania pliku z odwołaniem projektu do zestawu "<assemblyname>"
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 0f2e7040de5ea74f3793129d23d4ae8c80b71f25
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841553"
---
# <a name="message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a>\<komunikat > tego błędu może być również ze względu na połączenie odwołania pliku z odwołaniem projektu do zestawu "\<nazwa_zestawu >"
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
