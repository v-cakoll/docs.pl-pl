---
title: "Wymagane odwołanie do zestawu &#39; &lt;assemblyidentity&gt;&#39; zawierający typ &#39;&lt; Właściwość TypeName&gt;&#39; ale nie można odnaleźć pasującego odwołania z powodu niejednoznaczności między projektami &#39;&lt; projectname1&gt;&#39; i &#39;&lt; projectname2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords: BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ca2454f5c306b3defd1c885dfd59ee130f3e828
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a>Wymagane odwołanie do zestawu &#39; &lt;assemblyidentity&gt;&#39; zawierający typ &#39;&lt; Właściwość TypeName&gt;&#39; ale nie można odnaleźć pasującego odwołania z powodu niejednoznaczności między projektami &#39;&lt; projectname1&gt;&#39; i &#39;&lt; projectname2&gt;&#39;
Wyrażenie korzysta z typu, takich jak klasy, struktury, interfejsu, wyliczenie lub delegata, który jest zdefiniowany poza projektem. Jednak masz odwołań do więcej niż jeden zestaw definiujący ten typ projektu.  
  
 Projekty cytowane utworzyć zestawów o takiej samej nazwie. W związku z tym kompilator nie może określić uzyskują dostęp do zestawu, które do użycia dla typu.  
  
 Dostęp do typu zdefiniowanego w innym zestawie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora musi mieć odwołanie do tego zestawu. Musi to być pojedynczą, jednoznaczne odwołanie, które nie powoduje cykliczne odwołania między projektami.  
  
 **Identyfikator błędu:** BC30969  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Określ, który projekt tworzy najlepsze zestawu dla projektu do odwołania. Do tej decyzji można użyć kryteriów, takich jak łatwość dostępu do plików i częstotliwość aktualizacji.  
  
2.  We właściwościach projektu Dodaj odwołanie do pliku, który zawiera zestaw, który definiuje typ, którego używasz.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)  
 [Odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)  
 [Rozwiązywanie problemów z przerwanymi odwołaniami](/visualstudio/ide/troubleshooting-broken-references)
