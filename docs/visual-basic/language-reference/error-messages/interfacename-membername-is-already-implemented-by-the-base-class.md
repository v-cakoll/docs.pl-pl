---
title: "'<interfacename>. <membername>\"został już zaimplementowany przez klasę bazową\"<baseclassname>\". Ponowną implementację elementu <type> zakłada, że"
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 64bd7771820c2a4073350b7a5189d3a32c4775be
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832368"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a><span data-ttu-id="f751e-103">"\<interfacename >. \<membername > "został już zaimplementowany przez klasę bazową\<baseclassname >".</span><span class="sxs-lookup"><span data-stu-id="f751e-103">'\<interfacename>.\<membername>' is already implemented by the base class '\<baseclassname>'.</span></span> <span data-ttu-id="f751e-104">Ponowną implementację elementu \<typ > zakłada, że</span><span class="sxs-lookup"><span data-stu-id="f751e-104">Re-implementation of \<type> assumed</span></span>
<span data-ttu-id="f751e-105">Właściwość, procedura lub zdarzenia w klasie pochodnej używa `Implements` klauzulę określania składowej interfejsu, który został już zaimplementowany w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="f751e-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="f751e-106">Klasa pochodna może ponownie składowej interfejsu, który jest implementowany przez jej klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="f751e-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="f751e-107">Nie jest taka sama jak zastępowanie implementacji klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="f751e-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="f751e-108">Aby uzyskać więcej informacji, zobacz [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f751e-108">For more information, see [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="f751e-109">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="f751e-109">By default, this message is a warning.</span></span> <span data-ttu-id="f751e-110">Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f751e-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f751e-111">**Identyfikator błędu:** BC42015</span><span class="sxs-lookup"><span data-stu-id="f751e-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f751e-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="f751e-112">To correct this error</span></span>  
  
-   <span data-ttu-id="f751e-113">Jeśli planujesz ponownie składowej interfejsu, nie musisz podejmować żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="f751e-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="f751e-114">Kod w klasie pochodnej uzyskuje dostęp do składowej reimplemented chyba że używasz `MyBase` — słowo kluczowe do dostępu do implementacji klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="f751e-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
-   <span data-ttu-id="f751e-115">Jeśli nie zamierzasz ponownie składowej interfejsu, Usuń `Implements` klauzuli z deklaracji właściwość, procedura lub zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="f751e-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f751e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f751e-116">See also</span></span>

- [<span data-ttu-id="f751e-117">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="f751e-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
