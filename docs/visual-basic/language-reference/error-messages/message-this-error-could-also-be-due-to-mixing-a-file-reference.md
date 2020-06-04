---
title: <message> Przyczyną tego błędu może być również połączenie odwołania pliku z odwołaniem projektu do zestawu „<assemblyname>"
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 263e30f992ef58b0053acb2fd749d0d9186ef6b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397262"
---
# <a name="message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a>\<message> Przyczyną tego błędu może być również połączenie odwołania pliku z odwołaniem projektu do zestawu „\<assemblyname>"
\<message>Ten błąd może również być spowodowany mieszaniem odwołania do pliku z odwołaniem projektu do zestawu " \<assemblyname> . W takim przypadku Spróbuj zastąpić odwołanie do pliku " \<assemblyfilename> " w projekcie " \<projectname1> " z odwołaniem projektu do " \<projectname2> ".  
  
 Kod w projekcie uzyskuje dostęp do elementu członkowskiego innego projektu, ale Konfiguracja rozwiązania nie zezwala kompilatorowi Visual Basicemu na rozpoznanie odwołania.  
  
 Aby uzyskać dostęp do typu zdefiniowanego w innym zestawie, kompilator Visual Basic musi mieć odwołanie do tego zestawu. Musi to być jedno, niejednoznaczne odwołanie, które nie powoduje cyklicznych odwołań między projektami.  
  
 **Identyfikator błędu:** BC30971  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Ustal, który projekt tworzy najlepszy zestaw dla projektu do odwołania. W przypadku tej decyzji można użyć kryteriów, takich jak łatwość dostępu do plików i częstotliwość aktualizacji.  
  
2. We właściwościach projektu Dodaj odwołanie do projektu zawierającego zestaw, który definiuje używany typ.  
  
## <a name="see-also"></a>Zobacz też

- [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)
- [Odwołania do elementów zadeklarowanych](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
- [Rozwiązywanie problemów z przerwanymi odwołaniami](/visualstudio/ide/troubleshooting-broken-references)
