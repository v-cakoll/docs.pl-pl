---
title: 'Instrukcje: Dzielenie się zestawem z innymi aplikacjami (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
ms.openlocfilehash: 520fe69d30ca55251ae7a19dcd7a1ea0c11e7bd5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022184"
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="d55bc-102">Instrukcje: Dzielenie się zestawem z innymi aplikacjami (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d55bc-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="d55bc-103">Zestawy mogą być prywatne lub udostępnione: domyślnie większości programów proste składają się z zestawu prywatnego, ponieważ nie są przeznaczone do użycia przez inne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="d55bc-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="d55bc-104">Aby można było dzielenie się zestawem z innymi aplikacjami, muszą być umieszczone w [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="d55bc-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="d55bc-105">Współużytkowanie zestawu</span><span class="sxs-lookup"><span data-stu-id="d55bc-105">Sharing an assembly</span></span>  
  
1. <span data-ttu-id="d55bc-106">Utwórz zestaw.</span><span class="sxs-lookup"><span data-stu-id="d55bc-106">Create your assembly.</span></span> <span data-ttu-id="d55bc-107">Aby uzyskać więcej informacji, zobacz [tworzenia zestawów](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="d55bc-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2. <span data-ttu-id="d55bc-108">Do zestawu, należy przypisać silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="d55bc-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="d55bc-109">Aby uzyskać więcej informacji, zobacz [jak: Podpisywanie zestawu silną nazwą](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="d55bc-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3. <span data-ttu-id="d55bc-110">Informacje o wersji należy przypisać do swojego zestawu.</span><span class="sxs-lookup"><span data-stu-id="d55bc-110">Assign version information to your assembly.</span></span> <span data-ttu-id="d55bc-111">Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](../../../../framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="d55bc-111">For more information, see [Assembly Versioning](../../../../framework/app-domains/assembly-versioning.md).</span></span>  
  
4. <span data-ttu-id="d55bc-112">Dodaj zestaw do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="d55bc-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="d55bc-113">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie zestawu w globalnej pamięci podręcznej](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="d55bc-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5. <span data-ttu-id="d55bc-114">Dostęp do typów są zawarte w zestawie z innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d55bc-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="d55bc-115">Aby uzyskać więcej informacji, zobacz [jak: Odwołanie do zestawu o silnej nazwie](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="d55bc-115">For more information, see [How to: Reference a Strong-Named Assembly](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d55bc-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d55bc-116">See also</span></span>

- [<span data-ttu-id="d55bc-117">Pojęcia związane z programowaniem</span><span class="sxs-lookup"><span data-stu-id="d55bc-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="d55bc-118">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="d55bc-118">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="d55bc-119">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="d55bc-119">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
