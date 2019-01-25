---
title: 'Instrukcje: Ręczne tworzenie otok'
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fba0de3f45afc199255dce93e69142724b68b0fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553038"
---
# <a name="how-to-create-wrappers-manually"></a><span data-ttu-id="37569-102">Instrukcje: Ręczne tworzenie otok</span><span class="sxs-lookup"><span data-stu-id="37569-102">How to: Create Wrappers Manually</span></span>
<span data-ttu-id="37569-103">Jeśli zdecydujesz się zadeklarować typy modelu COM ręcznie, w zarządzanym kodzie źródłowym, najlepszym miejscem do rozpoczęcia jest istniejący plik Języka definicji interfejsu (IDL) lub biblioteka typów.</span><span class="sxs-lookup"><span data-stu-id="37569-103">If you decide to declare COM types manually in managed source code, the best place to start is with an existing Interface Definition Language (IDL) file or type library.</span></span> <span data-ttu-id="37569-104">Jeśli nie posiadasz pliku IDL ani nie możesz wygenerować pliku biblioteki typów, możesz zasymulować typy modelu COM przez utworzenie deklaracji zarządzanych i wyeksportowanie zestawu wynikowego do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="37569-104">When you do not have the IDL file or cannot generate a type library file, you can simulate the COM types by creating managed declarations and exporting the resulting assembly to a type library.</span></span>  
  
### <a name="to-simulate-com-types-from-managed-source"></a><span data-ttu-id="37569-105">Aby zasymulować typy modelu COM ze źródła zarządzanego</span><span class="sxs-lookup"><span data-stu-id="37569-105">To simulate COM types from managed source</span></span>  
  
1.  <span data-ttu-id="37569-106">Zadeklaruj typy w języku, który jest zgodny z Common Language Specification (CLS) i skompiluj plik.</span><span class="sxs-lookup"><span data-stu-id="37569-106">Declare the types in a language that is compliant with the Common Language Specification (CLS) and compile the file.</span></span>  
  
2.  <span data-ttu-id="37569-107">Wyeksportuj zestaw zawierający typy za pomocą [Eksporter biblioteki typów (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="37569-107">Export the assembly containing the types with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
3.  <span data-ttu-id="37569-108">Użyj wyeksportowanej biblioteki typów modelu COM jako podstawy do deklaracji typów zarządzanych zorientowanych na model COM.</span><span class="sxs-lookup"><span data-stu-id="37569-108">Use the exported COM type library as a basis for declaring COM-oriented managed types.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a><span data-ttu-id="37569-109">Aby utworzyć otokę wywoływaną w czasie wykonywania (RCW)</span><span class="sxs-lookup"><span data-stu-id="37569-109">To create a runtime callable wrapper (RCW)</span></span>  
  
1.  <span data-ttu-id="37569-110">Zakładając, że posiadasz plik IDL lub plik biblioteki typów, musisz zdecydować, które klasy i interfejsy mają zostać dołączone do niestandardowej RCW.</span><span class="sxs-lookup"><span data-stu-id="37569-110">Assuming that you have an IDL file or type library file, decide which classes and interfaces you want to include in the custom RCW.</span></span> <span data-ttu-id="37569-111">Możesz wykluczyć wszelkie typy, których nie zamierzasz używać w aplikacji bezpośrednio ani pośrednio.</span><span class="sxs-lookup"><span data-stu-id="37569-111">You can exclude any types that you do not intend to use directly or indirectly in your application.</span></span>  
  
2.  <span data-ttu-id="37569-112">Utwórz plik źródłowy w języku zgodnym ze specyfikacją CLS i zadeklaruj typy.</span><span class="sxs-lookup"><span data-stu-id="37569-112">Create a source file in a CLS-compliant language and declare the types.</span></span> <span data-ttu-id="37569-113">Zobacz [biblioteki typów na zestaw konwersja — Podsumowanie](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100)) pełny opis procesu konwersji importowania.</span><span class="sxs-lookup"><span data-stu-id="37569-113">See [Type Library to Assembly Conversion Summary](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100)) for a complete description of the import conversion process.</span></span> <span data-ttu-id="37569-114">Skutecznie, tworząc niestandardową otokę RCW, ręcznie wykonujesz działanie konwersji typu dostarczonego przez [Importer biblioteki typów (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="37569-114">Effectively, when you create a custom RCW, you are manually performing the type conversion activity provided by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="37569-115">W przykładzie znajdującym się w następnej sekcji pokazano typy w pliku IDL lub pliku biblioteki typów oraz odpowiadające typy w kodzie języka C#.</span><span class="sxs-lookup"><span data-stu-id="37569-115">The example in the next section shows types in an IDL or type library file and their corresponding types in C# code.</span></span>  
  
3.  <span data-ttu-id="37569-116">Gdy deklaracje będą kompletne, skompiluj plik, tak jak kompilujesz dowolny plik z zarządzanym kodem źródłowym.</span><span class="sxs-lookup"><span data-stu-id="37569-116">When the declarations are complete, compile the file as you compile any other managed source code.</span></span>  
  
4.  <span data-ttu-id="37569-117">Podobnie jak w przypadku typów importowanych za pomocą narzędzia Tlbimp.exe, niektóre typy wymagają dodatkowych informacji, które możesz dodać bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="37569-117">As with the types imported with Tlbimp.exe, some require additional information, which you can add directly to your code.</span></span> <span data-ttu-id="37569-118">Aby uzyskać więcej informacji, zobacz [jak: Edytowanie zestawów międzyoperacyjnych](https://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="37569-118">For details, see [How to: Edit Interop Assemblies](https://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="37569-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="37569-119">Example</span></span>  
 <span data-ttu-id="37569-120">W poniższym kodzie pokazano przykład interfejsu `ISATest` i klasy `SATest` napisane w języku IDL oraz odpowiadające typy w kodzie źródłowym języka C#.</span><span class="sxs-lookup"><span data-stu-id="37569-120">The following code shows an example of the `ISATest` interface and `SATest` class in IDL and the corresponding types in C# source code.</span></span>  
  
 <span data-ttu-id="37569-121">**IDL lub typu pliku biblioteki**</span><span class="sxs-lookup"><span data-stu-id="37569-121">**IDL or type library file**</span></span>  
  
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
  
 <span data-ttu-id="37569-122">**Otoka w zarządzanym kodzie źródłowym**</span><span class="sxs-lookup"><span data-stu-id="37569-122">**Wrapper in managed source code**</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="37569-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37569-123">See also</span></span>
- <span data-ttu-id="37569-124">[Dostosowywanie wywoływanych otok środowiska uruchomieniowego](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="37569-124">[Customizing Runtime Callable Wrappers](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100))</span></span>
- <span data-ttu-id="37569-125">[Typy danych COM](https://msdn.microsoft.com/library/f93ae35d-a416-4218-8700-c8218cc90061(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="37569-125">[COM Data Types](https://msdn.microsoft.com/library/f93ae35d-a416-4218-8700-c8218cc90061(v=vs.100))</span></span>
- <span data-ttu-id="37569-126">[Instrukcje: Edytowanie zestawów międzyoperacyjnych](https://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="37569-126">[How to: Edit Interop Assemblies](https://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277(v=vs.100))</span></span>
- <span data-ttu-id="37569-127">[Biblioteki typów na zestaw konwersja — podsumowanie](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="37569-127">[Type Library to Assembly Conversion Summary](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100))</span></span>
- [<span data-ttu-id="37569-128">Tlbimp.exe (importer biblioteki typów)</span><span class="sxs-lookup"><span data-stu-id="37569-128">Tlbimp.exe (Type Library Importer)</span></span>](../tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="37569-129">Tlbexp.exe (eksporter biblioteki typów)</span><span class="sxs-lookup"><span data-stu-id="37569-129">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
