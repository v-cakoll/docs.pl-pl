---
title: Wymagane odwołanie do zestawu &#39; &lt;assemblyidentity&gt; &#39; zawierający typ &#39; &lt;typename&gt;&#39;, ale nie można odnaleźć pasującego odwołania z powodu niejednoznaczności między Projekty &#39; &lt;projectname1&gt; &#39; i &#39; &lt;projectname2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 670ac3ceb6a703a11b8f00a341dbcf868d4ceb7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a>Wymagane odwołanie do zestawu &#39; &lt;assemblyidentity&gt; &#39; zawierający typ &#39; &lt;typename&gt;&#39;, ale nie można odnaleźć pasującego odwołania z powodu niejednoznaczności między Projekty &#39; &lt;projectname1&gt; &#39; i &#39; &lt;projectname2&gt;&#39;
Wyrażenie korzysta z typu, takich jak klasy, struktury, interfejsu, wyliczenie lub delegata, który jest zdefiniowany poza projektem. Jednak masz odwołań do więcej niż jeden zestaw definiujący ten typ projektu.  
  
 Projekty cytowane utworzyć zestawów o takiej samej nazwie. W związku z tym kompilator nie może określić uzyskują dostęp do zestawu, które do użycia dla typu.  
  
 Dostęp do typu zdefiniowanego w innym zestawie, kompilator Visual Basic musi mieć odwołanie do tego zestawu. Musi to być pojedynczą, jednoznaczne odwołanie, które nie powoduje cykliczne odwołania między projektami.  
  
 **Identyfikator błędu:** BC30969  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Określ, który projekt tworzy najlepsze zestawu dla projektu do odwołania. Do tej decyzji można użyć kryteriów, takich jak łatwość dostępu do plików i częstotliwość aktualizacji.  
  
2.  We właściwościach projektu Dodaj odwołanie do pliku, który zawiera zestaw, który definiuje typ, którego używasz.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)  
 [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)  
 [Rozwiązywanie problemów z przerwanymi odwołaniami](/visualstudio/ide/troubleshooting-broken-references)
