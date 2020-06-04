---
title: Klasa „<interfacename><membername>” jest już zaimplementowana przez klasę podstawową „<baseclassname>”. Przyjęto ponowną implementację elementu „<type>”
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 6525ae08b90cc530a8f6a469d35d9ab8c27fb5e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402827"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a><span data-ttu-id="c7d90-103">Klasa „\<interfacename>\<membername>” jest już zaimplementowana przez klasę podstawową „\<baseclassname>”.</span><span class="sxs-lookup"><span data-stu-id="c7d90-103">'\<interfacename>.\<membername>' is already implemented by the base class '\<baseclassname>'.</span></span> <span data-ttu-id="c7d90-104">Przyjęto ponowną implementację elementu „\<type>”</span><span class="sxs-lookup"><span data-stu-id="c7d90-104">Re-implementation of \<type> assumed</span></span>
<span data-ttu-id="c7d90-105">Właściwość, procedura lub zdarzenie w klasie pochodnej używa `Implements` klauzuli określającej element członkowski interfejsu, który jest już zaimplementowany w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="c7d90-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="c7d90-106">Klasa pochodna może zmienić implementację elementu członkowskiego interfejsu, który jest implementowany przez jego klasę bazową.</span><span class="sxs-lookup"><span data-stu-id="c7d90-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="c7d90-107">Ta wartość nie jest taka sama jak zastępowanie implementacji klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="c7d90-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="c7d90-108">Aby uzyskać więcej informacji, zobacz [Implements](../statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c7d90-108">For more information, see [Implements](../statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="c7d90-109">Domyślnie ten komunikat jest ostrzeżeniem.</span><span class="sxs-lookup"><span data-stu-id="c7d90-109">By default, this message is a warning.</span></span> <span data-ttu-id="c7d90-110">Aby uzyskać informacje na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c7d90-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c7d90-111">**Identyfikator błędu:** BC42015</span><span class="sxs-lookup"><span data-stu-id="c7d90-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c7d90-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c7d90-112">To correct this error</span></span>  
  
- <span data-ttu-id="c7d90-113">Jeśli zamierzasz ponownie zaimplementować element członkowski interfejsu, nie musisz podejmować żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="c7d90-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="c7d90-114">Kod w klasie pochodnej uzyskuje dostęp do zaimplementowanego elementu członkowskiego, chyba że użyjesz `MyBase` słowa kluczowego, aby uzyskać dostęp do implementacji klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="c7d90-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
- <span data-ttu-id="c7d90-115">Jeśli nie zamierzasz przeprowadzić ponownej implementacji elementu członkowskiego interfejsu, Usuń `Implements` klauzulę z właściwości, procedury lub deklaracji zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c7d90-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d90-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7d90-116">See also</span></span>

- [<span data-ttu-id="c7d90-117">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c7d90-117">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
