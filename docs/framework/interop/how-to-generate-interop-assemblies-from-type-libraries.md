---
title: 'Instrukcje: Generowanie zestawów międzyoperacyjnych z bibliotek typów'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cc388d68e5314604d3c8e8991b7fa3c600a5d873
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116730"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="e5b16-102">Instrukcje: Generowanie zestawów międzyoperacyjnych z bibliotek typów</span><span class="sxs-lookup"><span data-stu-id="e5b16-102">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="e5b16-103">[Importer biblioteki typów (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) jest narzędziem wiersza polecenia, który konwertuje klasy coclass i interfejsy zawarte w bibliotece typów modelu COM w metadanych.</span><span class="sxs-lookup"><span data-stu-id="e5b16-103">The [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="e5b16-104">To narzędzie automatycznie tworzy zestaw międzyoperacyjny i przestrzeni nazw, aby uzyskać informacje o typie.</span><span class="sxs-lookup"><span data-stu-id="e5b16-104">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="e5b16-105">Po udostępnieniu metadanych klas zarządzanych klientów można tworzenia wystąpień tego typu COM i wywołać jego metody tak, jakby był to wystąpienie programu .NET.</span><span class="sxs-lookup"><span data-stu-id="e5b16-105">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="e5b16-106">Tlbimp.exe konwertuje metadanych całej biblioteki typów na raz i nie można wygenerować informacji o typie dla podzbioru typów zdefiniowanych w bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="e5b16-106">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="e5b16-107">Do generowania zestawu międzyoperacyjnego z biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="e5b16-107">To generate an interop assembly from a type library</span></span>  
  
1.  <span data-ttu-id="e5b16-108">Użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="e5b16-108">Use the following command:</span></span>  
  
     <span data-ttu-id="e5b16-109">**tlbimp** \<*type-library-file*></span><span class="sxs-lookup"><span data-stu-id="e5b16-109">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="e5b16-110">Dodawanie **/out:** przełącznika tworzy zestaw międzyoperacyjny nazwą zmieniony, takich jak LOANLib.dll.</span><span class="sxs-lookup"><span data-stu-id="e5b16-110">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="e5b16-111">Zmienianie nazwy zestawu międzyoperacyjnego może pomóc odróżnić go od oryginalnego DLL modelu COM i uniemożliwić problemy, które mogą wystąpić o takich samych nazwach.</span><span class="sxs-lookup"><span data-stu-id="e5b16-111">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5b16-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="e5b16-112">Example</span></span>  
 <span data-ttu-id="e5b16-113">Następujące polecenie generuje zestaw Loanlib.dll na `Loanlib` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e5b16-113">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```  
tlbimp Loanlib.tlb  
```  
  
 <span data-ttu-id="e5b16-114">Następujące polecenie generuje zestaw międzyoperacyjny nazwą zmienionego (LOANLib.dll).</span><span class="sxs-lookup"><span data-stu-id="e5b16-114">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5b16-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5b16-115">See also</span></span>

- [<span data-ttu-id="e5b16-116">Importowanie biblioteki typów jako zestawu</span><span class="sxs-lookup"><span data-stu-id="e5b16-116">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="e5b16-117">Udostępnianie składników COM programowi.NET Framework</span><span class="sxs-lookup"><span data-stu-id="e5b16-117">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)
