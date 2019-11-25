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
ms.openlocfilehash: f4f099dfaf5ff02edd3958d7eab9354ce727a239
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281805"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="462fe-102">Porada: generowanie zestawów międzyoperacyjnych z bibliotek typów</span><span class="sxs-lookup"><span data-stu-id="462fe-102">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="462fe-103">[Importer biblioteki typów (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md) jest narzędziem wiersza polecenia, które konwertuje klasy coclass i interfejsy zawarte w bibliotece typów modelu COM na metadane.</span><span class="sxs-lookup"><span data-stu-id="462fe-103">The [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="462fe-104">To narzędzie tworzy zestaw międzyoperacyjny i przestrzeń nazw dla informacji o typie automatycznie.</span><span class="sxs-lookup"><span data-stu-id="462fe-104">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="462fe-105">Po udostępnieniu metadanych klasy zarządzani klienci mogą tworzyć wystąpienia typu COM i wywoływać metody, tak jakby były wystąpieniem programu .NET.</span><span class="sxs-lookup"><span data-stu-id="462fe-105">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="462fe-106">Tlbimp. exe konwertuje całą bibliotekę typów na metadane jednocześnie i nie może generować informacji o typie dla podzbioru typów zdefiniowanych w bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="462fe-106">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="462fe-107">Aby wygenerować zestaw międzyoperacyjny z biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="462fe-107">To generate an interop assembly from a type library</span></span>  
  
1. <span data-ttu-id="462fe-108">Użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="462fe-108">Use the following command:</span></span>  
  
     <span data-ttu-id="462fe-109">**tlbimp** \<*typ biblioteki*></span><span class="sxs-lookup"><span data-stu-id="462fe-109">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="462fe-110">Dodanie przełącznika **/out:** powoduje utworzenie zestawu międzyoperacyjnego o zmienionej nazwie, takiej jak LOANLib. dll.</span><span class="sxs-lookup"><span data-stu-id="462fe-110">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="462fe-111">Zmiana nazwy zestawu międzyoperacyjnego może pomóc w odróżnieniu od oryginalnej biblioteki DLL modelu COM i zapobiec problemom, które mogą wystąpić w przypadku zduplikowanych nazw.</span><span class="sxs-lookup"><span data-stu-id="462fe-111">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="462fe-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="462fe-112">Example</span></span>  
 <span data-ttu-id="462fe-113">Następujące polecenie generuje zestaw LOANLib. dll w przestrzeni nazw `Loanlib`.</span><span class="sxs-lookup"><span data-stu-id="462fe-113">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```console  
tlbimp Loanlib.tlb  
```  
  
 <span data-ttu-id="462fe-114">Następujące polecenie tworzy zestaw międzyoperacyjny z zmienioną nazwą (LOANLib. dll).</span><span class="sxs-lookup"><span data-stu-id="462fe-114">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```console  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="462fe-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="462fe-115">See also</span></span>

- [<span data-ttu-id="462fe-116">Importowanie biblioteki typów jako zestawu</span><span class="sxs-lookup"><span data-stu-id="462fe-116">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="462fe-117">Udostępnianie składników COM programowi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="462fe-117">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
