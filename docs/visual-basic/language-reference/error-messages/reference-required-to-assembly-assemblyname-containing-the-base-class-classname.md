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
ms.openlocfilehash: f7413c82a9c61d13e7ca6fa18f27a4769a0937f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="reference-required-to-assembly-39ltassemblynamegt39-containing-the-base-class-39ltclassnamegt39"></a><span data-ttu-id="423bf-102">Wymagane odwołanie do zestawu &#39; &lt;assemblyname&gt;&#39; zawierający klasę podstawową &#39;&lt; ClassName&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="423bf-102">Reference required to assembly &#39;&lt;assemblyname&gt;&#39; containing the base class &#39;&lt;classname&gt;&#39;</span></span>
<span data-ttu-id="423bf-103">Wymagane odwołanie do zestawu "\<assemblyname >" zawierającego klasę podstawową\<classname > ".</span><span class="sxs-lookup"><span data-stu-id="423bf-103">Reference required to assembly '\<assemblyname>' containing the base class '\<classname>'.</span></span> <span data-ttu-id="423bf-104">Dodaj je do projektu.</span><span class="sxs-lookup"><span data-stu-id="423bf-104">Add one to your project.</span></span>  
  
 <span data-ttu-id="423bf-105">Klasa jest zdefiniowana w biblioteki dołączanej (dynamicznie DLL) lub zestawu, który nie jest bezpośrednio wywoływany w projekcie.</span><span class="sxs-lookup"><span data-stu-id="423bf-105">The class is defined in a dynamic-link library (DLL) or assembly that is not directly referenced in your project.</span></span> <span data-ttu-id="423bf-106">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora wymaga odwołania, aby uniknąć niejednoznaczności w przypadku, gdy klasa jest zdefiniowana w więcej niż jednego pliku DLL lub zestawu.</span><span class="sxs-lookup"><span data-stu-id="423bf-106">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler requires a reference to avoid ambiguity in case the class is defined in more than one DLL or assembly.</span></span>  
  
 <span data-ttu-id="423bf-107">**Identyfikator błędu:** BC30007</span><span class="sxs-lookup"><span data-stu-id="423bf-107">**Error ID:** BC30007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="423bf-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="423bf-108">To correct this error</span></span>  
  
-   <span data-ttu-id="423bf-109">Uwzględnij nazwę nieużywane biblioteki DLL lub zestawu w odwołaniach do projektu.</span><span class="sxs-lookup"><span data-stu-id="423bf-109">Include the name of the unreferenced DLL or assembly in your project references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="423bf-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="423bf-110">See Also</span></span>  
 [<span data-ttu-id="423bf-111">NIB porady: Dodawanie lub usuwanie odwołań za pomocą okno dialogowe Dodaj odwołanie</span><span class="sxs-lookup"><span data-stu-id="423bf-111">NIB How to: Add or Remove References By Using the Add Reference Dialog Box</span></span>](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [<span data-ttu-id="423bf-112">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="423bf-112">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="423bf-113">Rozwiązywanie problemów z przerwanymi odwołaniami</span><span class="sxs-lookup"><span data-stu-id="423bf-113">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
