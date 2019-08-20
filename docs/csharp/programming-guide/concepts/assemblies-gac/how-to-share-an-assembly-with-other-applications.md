---
title: 'Instrukcje: Udostępnianie zestawu innym aplikacjom (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 954db3fe139ff307386fc182dbf16c60ce86bd30
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595730"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a><span data-ttu-id="dc7f9-102">Instrukcje: Udostępnianie zestawu innym aplikacjom (C#)</span><span class="sxs-lookup"><span data-stu-id="dc7f9-102">How to: Share an Assembly with Other Applications (C#)</span></span>
<span data-ttu-id="dc7f9-103">Zestawy mogą być prywatne lub udostępnione: Domyślnie większość prostych programów składa się z zestawu prywatnego, ponieważ nie są przeznaczone do użytku przez inne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="dc7f9-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="dc7f9-104">W celu udostępnienia zestawu innym aplikacjom należy umieścić je w [globalnej pamięci podręcznej zestawów](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="dc7f9-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="dc7f9-105">Udostępnianie zestawu</span><span class="sxs-lookup"><span data-stu-id="dc7f9-105">Sharing an assembly</span></span>  
  
1. <span data-ttu-id="dc7f9-106">Utwórz zestaw.</span><span class="sxs-lookup"><span data-stu-id="dc7f9-106">Create your assembly.</span></span> <span data-ttu-id="dc7f9-107">Aby uzyskać więcej informacji, zobacz [Tworzenie zestawów](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="dc7f9-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2. <span data-ttu-id="dc7f9-108">Przypisz silną nazwę do zestawu.</span><span class="sxs-lookup"><span data-stu-id="dc7f9-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="dc7f9-109">Aby uzyskać więcej informacji, zobacz [jak: Podpisz zestaw silną nazwą](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="dc7f9-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3. <span data-ttu-id="dc7f9-110">Przypisz informacje o wersji do Twojego zestawu.</span><span class="sxs-lookup"><span data-stu-id="dc7f9-110">Assign version information to your assembly.</span></span> <span data-ttu-id="dc7f9-111">Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](../../../../framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="dc7f9-111">For more information, see [Assembly Versioning](../../../../framework/app-domains/assembly-versioning.md).</span></span>  
  
4. <span data-ttu-id="dc7f9-112">Dodaj swój zestaw do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="dc7f9-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="dc7f9-113">Aby uzyskać więcej informacji, zobacz [jak: Zainstaluj zestaw w globalnej pamięci podręcznej](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)zestawów.</span><span class="sxs-lookup"><span data-stu-id="dc7f9-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5. <span data-ttu-id="dc7f9-114">Uzyskaj dostęp do typów zawartych w zestawie z innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc7f9-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="dc7f9-115">Aby uzyskać więcej informacji, zobacz [jak: Odwołuje się do zestawu](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md)o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="dc7f9-115">For more information, see [How to: Reference a Strong-Named Assembly](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc7f9-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc7f9-116">See also</span></span>

- [<span data-ttu-id="dc7f9-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="dc7f9-117">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="dc7f9-118">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="dc7f9-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
