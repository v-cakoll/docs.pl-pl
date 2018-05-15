---
title: 'Porada: generowanie zestawów międzyoperacyjnych z bibliotek typów'
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
ms.openlocfilehash: aea23daff28b50678b9fa7902857fc302494c4a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="e6297-102">Porada: generowanie zestawów międzyoperacyjnych z bibliotek typów</span><span class="sxs-lookup"><span data-stu-id="e6297-102">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="e6297-103">[Importer biblioteki typów (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) to narzędzie wiersza polecenia, który konwertuje klasy coclass i interfejsy zawartych w bibliotece typów COM do metadanych.</span><span class="sxs-lookup"><span data-stu-id="e6297-103">The [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="e6297-104">To narzędzie automatycznie tworzy zestaw międzyoperacyjny i przestrzeń nazw dla informacji o typie.</span><span class="sxs-lookup"><span data-stu-id="e6297-104">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="e6297-105">Po metadanych klasy jest dostępny, zarządzanych klientów można utworzyć wystąpienia typu COM i wywołanie jego metody, tak jakby był wystąpienia programu .NET.</span><span class="sxs-lookup"><span data-stu-id="e6297-105">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="e6297-106">Tlbimp.exe jednocześnie konwertuje biblioteki typów całego metadanych i nie można wygenerować informacji o typie dla podzbioru z typów definiowanych w bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="e6297-106">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="e6297-107">Do generowania zestawu międzyoperacyjnego z biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="e6297-107">To generate an interop assembly from a type library</span></span>  
  
1.  <span data-ttu-id="e6297-108">Użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="e6297-108">Use the following command:</span></span>  
  
     <span data-ttu-id="e6297-109">**tlbimp** \< *pliku biblioteki typów*></span><span class="sxs-lookup"><span data-stu-id="e6297-109">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="e6297-110">Dodawanie **/out:** przełącznika tworzy zestaw międzyoperacyjny nazwą zmieniony, takich jak LOANLib.dll.</span><span class="sxs-lookup"><span data-stu-id="e6297-110">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="e6297-111">Zmiana nazwy zestawu międzyoperacyjnego umożliwia odróżniający go od oryginalnego pliku DLL COM i uniemożliwić problemów, które mogą wystąpić o takich samych nazwach.</span><span class="sxs-lookup"><span data-stu-id="e6297-111">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6297-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="e6297-112">Example</span></span>  
 <span data-ttu-id="e6297-113">Następujące polecenie spowoduje utworzenie zestawu Loanlib.dll w `Loanlib` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e6297-113">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```  
tlbimp Loanlib.dll  
```  
  
 <span data-ttu-id="e6297-114">Następujące polecenie spowoduje utworzenie zestawu międzyoperacyjnego o zmienionej nazwie (LOANLib.dll).</span><span class="sxs-lookup"><span data-stu-id="e6297-114">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```  
tlbimp LoanLib.dll /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6297-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e6297-115">See Also</span></span>  
 [<span data-ttu-id="e6297-116">Importowanie biblioteki typów jako zestawu</span><span class="sxs-lookup"><span data-stu-id="e6297-116">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
 [<span data-ttu-id="e6297-117">Udostępnianie składników COM programowi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e6297-117">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)
