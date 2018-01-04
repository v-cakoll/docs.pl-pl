---
title: "Wymagane odwołanie do zestawu &#39; &lt;assemblyname&gt;&#39; zawierający klasę podstawową &#39;&lt; ClassName&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords: BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 39fa33a655b311ee39466c18cefdb0bf07a92720
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="reference-required-to-assembly-39ltassemblynamegt39-containing-the-base-class-39ltclassnamegt39"></a>Wymagane odwołanie do zestawu &#39; &lt;assemblyname&gt;&#39; zawierający klasę podstawową &#39;&lt; ClassName&gt;&#39;
Wymagane odwołanie do zestawu "\<assemblyname >" zawierającego klasę podstawową\<classname > ". Dodaj je do projektu.  
  
 Klasa jest zdefiniowana w biblioteki dołączanej (dynamicznie DLL) lub zestawu, który nie jest bezpośrednio wywoływany w projekcie. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora wymaga odwołania, aby uniknąć niejednoznaczności w przypadku, gdy klasa jest zdefiniowana w więcej niż jednego pliku DLL lub zestawu.  
  
 **Identyfikator błędu:** BC30007  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Uwzględnij nazwę nieużywane biblioteki DLL lub zestawu w odwołaniach do projektu.  
  
## <a name="see-also"></a>Zobacz też  
   
 [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)  
 [Rozwiązywanie problemów z przerwanymi odwołaniami](/visualstudio/ide/troubleshooting-broken-references)
