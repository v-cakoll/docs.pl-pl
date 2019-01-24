---
title: 'Instrukcje: Dzielenie się zestawem z innymi aplikacjami (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
ms.openlocfilehash: d0e1dafc700b55a63342331b3280337d2c93cbd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631831"
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="efb97-102">Instrukcje: Dzielenie się zestawem z innymi aplikacjami (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efb97-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="efb97-103">Zestawy mogą być prywatne lub udostępnione: domyślnie większości programów proste składają się z zestawu prywatnego, ponieważ nie są przeznaczone do użycia przez inne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="efb97-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="efb97-104">Aby można było dzielenie się zestawem z innymi aplikacjami, muszą być umieszczone w [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="efb97-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="efb97-105">Współużytkowanie zestawu</span><span class="sxs-lookup"><span data-stu-id="efb97-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="efb97-106">Utwórz zestaw.</span><span class="sxs-lookup"><span data-stu-id="efb97-106">Create your assembly.</span></span> <span data-ttu-id="efb97-107">Aby uzyskać więcej informacji, zobacz [tworzenia zestawów](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="efb97-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="efb97-108">Do zestawu, należy przypisać silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="efb97-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="efb97-109">Aby uzyskać więcej informacji, zobacz [jak: Podpisywanie zestawu silną nazwą](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="efb97-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="efb97-110">Informacje o wersji należy przypisać do swojego zestawu.</span><span class="sxs-lookup"><span data-stu-id="efb97-110">Assign version information to your assembly.</span></span> <span data-ttu-id="efb97-111">Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](../../../../framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="efb97-111">For more information, see [Assembly Versioning](../../../../framework/app-domains/assembly-versioning.md).</span></span>  
  
4.  <span data-ttu-id="efb97-112">Dodaj zestaw do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="efb97-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="efb97-113">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie zestawu w globalnej pamięci podręcznej](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="efb97-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="efb97-114">Dostęp do typów są zawarte w zestawie z innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="efb97-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="efb97-115">Aby uzyskać więcej informacji, zobacz [jak: Odwołanie do zestawu o silnej nazwie](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="efb97-115">For more information, see [How to: Reference a Strong-Named Assembly](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efb97-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efb97-116">See also</span></span>

- [<span data-ttu-id="efb97-117">Pojęcia związane z programowaniem</span><span class="sxs-lookup"><span data-stu-id="efb97-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="efb97-118">Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efb97-118">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
- [<span data-ttu-id="efb97-119">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="efb97-119">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
