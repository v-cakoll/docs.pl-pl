---
title: "&lt;komunikat&gt; tego błędu może być również spowodowane połączenie odwołania pliku z odwołaniem projektu do zestawu &#39;&lt; AssemblyName&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0fcbcc48928b1b03487f31930e3d14051ddd990a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a>&lt;komunikat&gt; tego błędu może być również spowodowane połączenie odwołania pliku z odwołaniem projektu do zestawu &#39;&lt; AssemblyName&gt;&#39;
\<komunikat > tego błędu może być również spowodowane połączenie odwołania pliku z odwołaniem projektu do zestawu "\<assemblyname >. W takim przypadku spróbuj zamienić odwołanie pliku do "\<assemblyfilename >" w projekcie "\<projectname1 >" na odwołanie projektu do "\<projectname2 >".  
  
 Członkiem innego projektu uzyskuje dostęp do kodu w projekcie, ale nie zezwala na konfigurację rozwiązania [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora rozpoznać odwołania.  
  
 Dostęp do typu zdefiniowanego w innym zestawie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora musi mieć odwołanie do tego zestawu. Musi to być pojedynczą, jednoznaczne odwołanie, które nie powoduje cykliczne odwołania między projektami.  
  
 **Identyfikator błędu:** BC30971  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Określ, który projekt tworzy najlepsze zestawu dla projektu do odwołania. Do tej decyzji można użyć kryteriów, takich jak łatwość dostępu do plików i częstotliwość aktualizacji.  
  
2.  We właściwościach projektu Dodaj odwołanie do projektu, który zawiera zestaw, który definiuje typ, którego używasz.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)  
 [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)  
 [Rozwiązywanie problemów z przerwanymi odwołaniami](/visualstudio/ide/troubleshooting-broken-references)
