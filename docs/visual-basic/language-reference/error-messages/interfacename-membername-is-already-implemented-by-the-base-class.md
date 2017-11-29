---
title: "&#39; &lt;interfacename&gt;.&lt; membername&gt;&#39; został już zaimplementowany przez klasę podstawową &#39;&lt; baseclassname&gt;&#39;. Ponowną implementację elementu &lt;typu&gt; założono, że"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords: BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69884ed567e0046da5cf5c51b3e83e57e890d49f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a><span data-ttu-id="5c36e-103">&#39; &lt;interfacename&gt;.&lt; membername&gt;&#39; został już zaimplementowany przez klasę podstawową &#39;&lt; baseclassname&gt;&#39;.</span><span class="sxs-lookup"><span data-stu-id="5c36e-103">&#39;&lt;interfacename&gt;.&lt;membername&gt;&#39; is already implemented by the base class &#39;&lt;baseclassname&gt;&#39;.</span></span> <span data-ttu-id="5c36e-104">Ponowną implementację elementu &lt;typu&gt; założono, że</span><span class="sxs-lookup"><span data-stu-id="5c36e-104">Re-implementation of &lt;type&gt; assumed</span></span>
<span data-ttu-id="5c36e-105">Właściwość, procedura lub zdarzenia w klasie pochodnej używa `Implements` klauzuli Określanie elementu członkowskiego interfejsu, który jest już zaimplementowana w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="5c36e-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="5c36e-106">Klasa pochodna może reimplement elementu członkowskiego interfejsu, który jest implementowany przez jej klasa podstawowa.</span><span class="sxs-lookup"><span data-stu-id="5c36e-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="5c36e-107">Nie jest taka sama jak zastępowanie implementacji klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="5c36e-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="5c36e-108">Aby uzyskać więcej informacji, zobacz [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5c36e-108">For more information, see [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="5c36e-109">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="5c36e-109">By default, this message is a warning.</span></span> <span data-ttu-id="5c36e-110">Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5c36e-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="5c36e-111">**Identyfikator błędu:** BC42015</span><span class="sxs-lookup"><span data-stu-id="5c36e-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5c36e-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="5c36e-112">To correct this error</span></span>  
  
-   <span data-ttu-id="5c36e-113">Jeśli zamierzasz reimplement elementu członkowskiego interfejsu, nie trzeba podejmować żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="5c36e-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="5c36e-114">Kod w klasie pochodnej uzyskuje dostęp do elementu członkowskiego reimplemented tylko w przypadku `MyBase` — słowo kluczowe do implementacji klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="5c36e-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
-   <span data-ttu-id="5c36e-115">Jeśli nie zamierzasz reimplement elementu członkowskiego interfejsu, Usuń `Implements` klauzuli z deklaracji właściwości, procedura lub zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5c36e-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c36e-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c36e-116">See Also</span></span>  
 [<span data-ttu-id="5c36e-117">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="5c36e-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
