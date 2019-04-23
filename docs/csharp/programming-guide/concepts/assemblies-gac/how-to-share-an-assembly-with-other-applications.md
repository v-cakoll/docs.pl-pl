---
title: 'Instrukcje: Dzielenie się zestawem z innymi aplikacjami (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 8bb36c2aded1144349b86b17a45eef4b48c8aabe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314792"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a><span data-ttu-id="9ed4b-102">Instrukcje: Dzielenie się zestawem z innymi aplikacjami (C#)</span><span class="sxs-lookup"><span data-stu-id="9ed4b-102">How to: Share an Assembly with Other Applications (C#)</span></span>
<span data-ttu-id="9ed4b-103">Zestawy mogą być prywatne lub udostępnione: domyślnie większości programów proste składają się z zestawu prywatnego, ponieważ nie są przeznaczone do użycia przez inne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="9ed4b-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="9ed4b-104">Aby można było dzielenie się zestawem z innymi aplikacjami, muszą być umieszczone w [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="9ed4b-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="9ed4b-105">Współużytkowanie zestawu</span><span class="sxs-lookup"><span data-stu-id="9ed4b-105">Sharing an assembly</span></span>  
  
1. <span data-ttu-id="9ed4b-106">Utwórz zestaw.</span><span class="sxs-lookup"><span data-stu-id="9ed4b-106">Create your assembly.</span></span> <span data-ttu-id="9ed4b-107">Aby uzyskać więcej informacji, zobacz [tworzenia zestawów](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="9ed4b-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2. <span data-ttu-id="9ed4b-108">Do zestawu, należy przypisać silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="9ed4b-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="9ed4b-109">Aby uzyskać więcej informacji, zobacz [jak: Podpisywanie zestawu silną nazwą](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="9ed4b-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3. <span data-ttu-id="9ed4b-110">Informacje o wersji należy przypisać do swojego zestawu.</span><span class="sxs-lookup"><span data-stu-id="9ed4b-110">Assign version information to your assembly.</span></span> <span data-ttu-id="9ed4b-111">Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](../../../../../docs/framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="9ed4b-111">For more information, see [Assembly Versioning](../../../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
4. <span data-ttu-id="9ed4b-112">Dodaj zestaw do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="9ed4b-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="9ed4b-113">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie zestawu w globalnej pamięci podręcznej](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="9ed4b-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5. <span data-ttu-id="9ed4b-114">Dostęp do typów są zawarte w zestawie z innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9ed4b-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="9ed4b-115">Aby uzyskać więcej informacji, zobacz [jak: Odwołanie do zestawu o silnej nazwie](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="9ed4b-115">For more information, see [How to: Reference a Strong-Named Assembly](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed4b-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ed4b-116">See also</span></span>

- [<span data-ttu-id="9ed4b-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9ed4b-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="9ed4b-118">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="9ed4b-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
