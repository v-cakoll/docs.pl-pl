---
title: '&#39;&lt;InterfaceName&gt;.&lt; membername&gt; &#39; został już zaimplementowany przez klasę bazową &#39; &lt;baseclassname&gt;&#39;. Ponowną implementację elementu &lt;typu&gt; zakłada, że'
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 22a3bd4e8c09c0d070e7fa5e75571a7215c3a274
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507203"
---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a><span data-ttu-id="d1ee7-103">&#39;&lt;InterfaceName&gt;.&lt; membername&gt; &#39; został już zaimplementowany przez klasę bazową &#39; &lt;baseclassname&gt;&#39;.</span><span class="sxs-lookup"><span data-stu-id="d1ee7-103">&#39;&lt;interfacename&gt;.&lt;membername&gt;&#39; is already implemented by the base class &#39;&lt;baseclassname&gt;&#39;.</span></span> <span data-ttu-id="d1ee7-104">Ponowną implementację elementu &lt;typu&gt; zakłada, że</span><span class="sxs-lookup"><span data-stu-id="d1ee7-104">Re-implementation of &lt;type&gt; assumed</span></span>
<span data-ttu-id="d1ee7-105">Właściwość, procedura lub zdarzenia w klasie pochodnej używa `Implements` klauzulę określania składowej interfejsu, który został już zaimplementowany w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="d1ee7-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="d1ee7-106">Klasa pochodna może ponownie składowej interfejsu, który jest implementowany przez jej klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="d1ee7-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="d1ee7-107">Nie jest taka sama jak zastępowanie implementacji klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="d1ee7-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="d1ee7-108">Aby uzyskać więcej informacji, zobacz [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d1ee7-108">For more information, see [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="d1ee7-109">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="d1ee7-109">By default, this message is a warning.</span></span> <span data-ttu-id="d1ee7-110">Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d1ee7-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d1ee7-111">**Identyfikator błędu:** BC42015</span><span class="sxs-lookup"><span data-stu-id="d1ee7-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d1ee7-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d1ee7-112">To correct this error</span></span>  
  
-   <span data-ttu-id="d1ee7-113">Jeśli planujesz ponownie składowej interfejsu, nie musisz podejmować żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="d1ee7-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="d1ee7-114">Kod w klasie pochodnej uzyskuje dostęp do składowej reimplemented chyba że używasz `MyBase` — słowo kluczowe do dostępu do implementacji klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="d1ee7-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
-   <span data-ttu-id="d1ee7-115">Jeśli nie zamierzasz ponownie składowej interfejsu, Usuń `Implements` klauzuli z deklaracji właściwość, procedura lub zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="d1ee7-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1ee7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1ee7-116">See also</span></span>
- [<span data-ttu-id="d1ee7-117">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d1ee7-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
