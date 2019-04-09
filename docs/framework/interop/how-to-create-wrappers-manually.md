---
title: 'Instrukcje: Ręczne tworzenie otok'
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d6959ac8b2315d928ab2ac362bb3b2c4081d46e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117108"
---
# <a name="how-to-create-wrappers-manually"></a><span data-ttu-id="c640d-102">Instrukcje: Ręczne tworzenie otok</span><span class="sxs-lookup"><span data-stu-id="c640d-102">How to: Create Wrappers Manually</span></span>
<span data-ttu-id="c640d-103">Jeśli zdecydujesz się zadeklarować typy modelu COM ręcznie, w zarządzanym kodzie źródłowym, najlepszym miejscem do rozpoczęcia jest istniejący plik Języka definicji interfejsu (IDL) lub biblioteka typów.</span><span class="sxs-lookup"><span data-stu-id="c640d-103">If you decide to declare COM types manually in managed source code, the best place to start is with an existing Interface Definition Language (IDL) file or type library.</span></span> <span data-ttu-id="c640d-104">Jeśli nie posiadasz pliku IDL ani nie możesz wygenerować pliku biblioteki typów, możesz zasymulować typy modelu COM przez utworzenie deklaracji zarządzanych i wyeksportowanie zestawu wynikowego do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="c640d-104">When you do not have the IDL file or cannot generate a type library file, you can simulate the COM types by creating managed declarations and exporting the resulting assembly to a type library.</span></span>  
  
### <a name="to-simulate-com-types-from-managed-source"></a><span data-ttu-id="c640d-105">Aby zasymulować typy modelu COM ze źródła zarządzanego</span><span class="sxs-lookup"><span data-stu-id="c640d-105">To simulate COM types from managed source</span></span>  
  
1.  <span data-ttu-id="c640d-106">Zadeklaruj typy w języku, który jest zgodny z Common Language Specification (CLS) i skompiluj plik.</span><span class="sxs-lookup"><span data-stu-id="c640d-106">Declare the types in a language that is compliant with the Common Language Specification (CLS) and compile the file.</span></span>  
  
2.  <span data-ttu-id="c640d-107">Wyeksportuj zestaw zawierający typy za pomocą [Eksporter biblioteki typów (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="c640d-107">Export the assembly containing the types with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
3.  <span data-ttu-id="c640d-108">Użyj wyeksportowanej biblioteki typów modelu COM jako podstawy do deklaracji typów zarządzanych zorientowanych na model COM.</span><span class="sxs-lookup"><span data-stu-id="c640d-108">Use the exported COM type library as a basis for declaring COM-oriented managed types.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a><span data-ttu-id="c640d-109">Aby utworzyć otokę wywoływaną w czasie wykonywania (RCW)</span><span class="sxs-lookup"><span data-stu-id="c640d-109">To create a runtime callable wrapper (RCW)</span></span>  
  
1.  <span data-ttu-id="c640d-110">Zakładając, że posiadasz plik IDL lub plik biblioteki typów, musisz zdecydować, które klasy i interfejsy mają zostać dołączone do niestandardowej RCW.</span><span class="sxs-lookup"><span data-stu-id="c640d-110">Assuming that you have an IDL file or type library file, decide which classes and interfaces you want to include in the custom RCW.</span></span> <span data-ttu-id="c640d-111">Możesz wykluczyć wszelkie typy, których nie zamierzasz używać w aplikacji bezpośrednio ani pośrednio.</span><span class="sxs-lookup"><span data-stu-id="c640d-111">You can exclude any types that you do not intend to use directly or indirectly in your application.</span></span>  
  
2.  <span data-ttu-id="c640d-112">Utwórz plik źródłowy w języku zgodnym ze specyfikacją CLS i zadeklaruj typy.</span><span class="sxs-lookup"><span data-stu-id="c640d-112">Create a source file in a CLS-compliant language and declare the types.</span></span> <span data-ttu-id="c640d-113">Zobacz [biblioteki typów na zestaw konwersja — Podsumowanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) pełny opis procesu konwersji importowania.</span><span class="sxs-lookup"><span data-stu-id="c640d-113">See [Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) for a complete description of the import conversion process.</span></span> <span data-ttu-id="c640d-114">Skutecznie, tworząc niestandardową otokę RCW, ręcznie wykonujesz działanie konwersji typu dostarczonego przez [Importer biblioteki typów (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="c640d-114">Effectively, when you create a custom RCW, you are manually performing the type conversion activity provided by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="c640d-115">W przykładzie znajdującym się w następnej sekcji pokazano typy w pliku IDL lub pliku biblioteki typów oraz odpowiadające typy w kodzie języka C#.</span><span class="sxs-lookup"><span data-stu-id="c640d-115">The example in the next section shows types in an IDL or type library file and their corresponding types in C# code.</span></span>  
  
3.  <span data-ttu-id="c640d-116">Gdy deklaracje będą kompletne, skompiluj plik, tak jak kompilujesz dowolny plik z zarządzanym kodem źródłowym.</span><span class="sxs-lookup"><span data-stu-id="c640d-116">When the declarations are complete, compile the file as you compile any other managed source code.</span></span>  
  
4.  <span data-ttu-id="c640d-117">Podobnie jak w przypadku typów importowanych za pomocą narzędzia Tlbimp.exe, niektóre typy wymagają dodatkowych informacji, które możesz dodać bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c640d-117">As with the types imported with Tlbimp.exe, some require additional information, which you can add directly to your code.</span></span> <span data-ttu-id="c640d-118">Aby uzyskać więcej informacji, zobacz [jak: Edytowanie zestawów międzyoperacyjnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c640d-118">For details, see [How to: Edit Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c640d-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="c640d-119">Example</span></span>  
 <span data-ttu-id="c640d-120">W poniższym kodzie pokazano przykład interfejsu `ISATest` i klasy `SATest` napisane w języku IDL oraz odpowiadające typy w kodzie źródłowym języka C#.</span><span class="sxs-lookup"><span data-stu-id="c640d-120">The following code shows an example of the `ISATest` interface and `SATest` class in IDL and the corresponding types in C# source code.</span></span>  
  
 **<span data-ttu-id="c640d-121">Plik IDL lub plik biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="c640d-121">IDL or type library file</span></span>**  
  
```  
 [  
object,  
uuid(40A8C65D-2448-447A-B786-64682CBEF133),  
dual,  
helpstring("ISATest Interface"),  
pointer_default(unique)  
 ]  
interface ISATest : IDispatch  
 {  
[id(1), helpstring("method InSArray")]   
HRESULT InSArray([in] SAFEARRAY(int) *ppsa, [out,retval] int *pSum);  
 };  
 [  
uuid(116CCA1E-7E39-4515-9849-90790DA6431E),  
helpstring("SATest Class")  
 ]  
coclass SATest  
 {  
  [default] interface ISATest;  
 };  
```  
  
 **<span data-ttu-id="c640d-122">Otoka w zarządzanym kodzie źródłowym</span><span class="sxs-lookup"><span data-stu-id="c640d-122">Wrapper in managed source code</span></span>**  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
using System.Runtime.CompilerServices;  
  
[assembly:Guid("E4A992B8-6F5C-442C-96E7-C4778924C753")]  
[assembly:ImportedFromTypeLib("SAServerLib")]  
namespace SAServer  
{  
 [ComImport]  
 [Guid("40A8C65D-2448-447A-B786-64682CBEF133")]  
 [TypeLibType(TypeLibTypeFlags.FLicensed)]  
 public interface ISATest  
 {  
  [DispId(1)]  
  //[MethodImpl(MethodImplOptions.InternalCall,  
  // MethodCodeType=MethodCodeType.Runtime)]  
  int InSArray( [MarshalAs(UnmanagedType.SafeArray,  
      SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }   
 [ComImport]  
 [Guid("116CCA1E-7E39-4515-9849-90790DA6431E")]  
 [ClassInterface(ClassInterfaceType.None)]  
 [TypeLibType(TypeLibTypeFlags.FCanCreate)]  
 public class SATest : ISATest  
 {  
  [DispId(1)]  
  [MethodImpl(MethodImplOptions.InternalCall,   
  MethodCodeType=MethodCodeType.Runtime)]  
  extern int ISATest.InSArray( [MarshalAs(UnmanagedType.SafeArray,   
  SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c640d-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c640d-123">See also</span></span>

- [<span data-ttu-id="c640d-124">Dostosowywanie wywoływanych otok środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="c640d-124">Customizing Runtime Callable Wrappers</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))
- [<span data-ttu-id="c640d-125">Typy danych COM</span><span class="sxs-lookup"><span data-stu-id="c640d-125">COM Data Types</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))
- [<span data-ttu-id="c640d-126">Instrukcje: Edytowanie zestawów międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="c640d-126">How to: Edit Interop Assemblies</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))
- [<span data-ttu-id="c640d-127">Podsumowanie informacji o konwersji biblioteki typów na zestaw</span><span class="sxs-lookup"><span data-stu-id="c640d-127">Type Library to Assembly Conversion Summary</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [<span data-ttu-id="c640d-128">Tlbimp.exe (Importer biblioteki typów)</span><span class="sxs-lookup"><span data-stu-id="c640d-128">Tlbimp.exe (Type Library Importer)</span></span>](../tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="c640d-129">Tlbexp.exe (Eksporter biblioteki typów)</span><span class="sxs-lookup"><span data-stu-id="c640d-129">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
