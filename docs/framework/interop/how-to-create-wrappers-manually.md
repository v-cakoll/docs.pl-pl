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
# <a name="how-to-create-wrappers-manually"></a>Instrukcje: Ręczne tworzenie otok
Jeśli zdecydujesz się zadeklarować typy modelu COM ręcznie, w zarządzanym kodzie źródłowym, najlepszym miejscem do rozpoczęcia jest istniejący plik Języka definicji interfejsu (IDL) lub biblioteka typów. Jeśli nie posiadasz pliku IDL ani nie możesz wygenerować pliku biblioteki typów, możesz zasymulować typy modelu COM przez utworzenie deklaracji zarządzanych i wyeksportowanie zestawu wynikowego do biblioteki typów.  
  
### <a name="to-simulate-com-types-from-managed-source"></a>Aby zasymulować typy modelu COM ze źródła zarządzanego  
  
1.  Zadeklaruj typy w języku, który jest zgodny z Common Language Specification (CLS) i skompiluj plik.  
  
2.  Wyeksportuj zestaw zawierający typy za pomocą [Eksporter biblioteki typów (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).  
  
3.  Użyj wyeksportowanej biblioteki typów modelu COM jako podstawy do deklaracji typów zarządzanych zorientowanych na model COM.  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a>Aby utworzyć otokę wywoływaną w czasie wykonywania (RCW)  
  
1.  Zakładając, że posiadasz plik IDL lub plik biblioteki typów, musisz zdecydować, które klasy i interfejsy mają zostać dołączone do niestandardowej RCW. Możesz wykluczyć wszelkie typy, których nie zamierzasz używać w aplikacji bezpośrednio ani pośrednio.  
  
2.  Utwórz plik źródłowy w języku zgodnym ze specyfikacją CLS i zadeklaruj typy. Zobacz [biblioteki typów na zestaw konwersja — Podsumowanie](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100)) pełny opis procesu konwersji importowania. Skutecznie, tworząc niestandardową otokę RCW, ręcznie wykonujesz działanie konwersji typu dostarczonego przez [Importer biblioteki typów (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md). W przykładzie znajdującym się w następnej sekcji pokazano typy w pliku IDL lub pliku biblioteki typów oraz odpowiadające typy w kodzie języka C#.  
  
3.  Gdy deklaracje będą kompletne, skompiluj plik, tak jak kompilujesz dowolny plik z zarządzanym kodem źródłowym.  
  
4.  Podobnie jak w przypadku typów importowanych za pomocą narzędzia Tlbimp.exe, niektóre typy wymagają dodatkowych informacji, które możesz dodać bezpośrednio w kodzie. Aby uzyskać więcej informacji, zobacz [jak: Edytowanie zestawów międzyoperacyjnych](https://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277(v=vs.100)).  
  
## <a name="example"></a>Przykład  
 W poniższym kodzie pokazano przykład interfejsu `ISATest` i klasy `SATest` napisane w języku IDL oraz odpowiadające typy w kodzie źródłowym języka C#.  
  
 **IDL lub typu pliku biblioteki**  
  
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
  
 **Otoka w zarządzanym kodzie źródłowym**  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Dostosowywanie wywoływanych otok środowiska uruchomieniowego](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100))
- [Typy danych COM](https://msdn.microsoft.com/library/f93ae35d-a416-4218-8700-c8218cc90061(v=vs.100))
- [Instrukcje: Edytowanie zestawów międzyoperacyjnych](https://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277(v=vs.100))
- [Biblioteki typów na zestaw konwersja — podsumowanie](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100))
- [Tlbimp.exe (importer biblioteki typów)](../tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (eksporter biblioteki typów)](../tools/tlbexp-exe-type-library-exporter.md)
