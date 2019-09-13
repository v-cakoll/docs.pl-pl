---
title: 'Instrukcje: Ręczne tworzenie otok'
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5db0ec9050c74b27d3ee25a99dcf8e2319835ffb
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894221"
---
# <a name="how-to-create-wrappers-manually"></a>Instrukcje: Ręczne tworzenie otok
Jeśli zdecydujesz się zadeklarować typy modelu COM ręcznie, w zarządzanym kodzie źródłowym, najlepszym miejscem do rozpoczęcia jest istniejący plik Języka definicji interfejsu (IDL) lub biblioteka typów. Jeśli nie posiadasz pliku IDL ani nie możesz wygenerować pliku biblioteki typów, możesz zasymulować typy modelu COM przez utworzenie deklaracji zarządzanych i wyeksportowanie zestawu wynikowego do biblioteki typów.  
  
### <a name="to-simulate-com-types-from-managed-source"></a>Aby zasymulować typy modelu COM ze źródła zarządzanego  
  
1. Zadeklaruj typy w języku, który jest zgodny z Common Language Specification (CLS) i skompiluj plik.  
  
2. Wyeksportuj zestaw zawierający typy z [eksporterem biblioteki typów (Tlbexp. exe)](../tools/tlbexp-exe-type-library-exporter.md).  
  
3. Użyj wyeksportowanej biblioteki typów modelu COM jako podstawy do deklaracji typów zarządzanych zorientowanych na model COM.  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a>Aby utworzyć otokę wywoływaną w czasie wykonywania (RCW)  
  
1. Zakładając, że posiadasz plik IDL lub plik biblioteki typów, musisz zdecydować, które klasy i interfejsy mają zostać dołączone do niestandardowej RCW. Możesz wykluczyć wszelkie typy, których nie zamierzasz używać w aplikacji bezpośrednio ani pośrednio.  
  
2. Utwórz plik źródłowy w języku zgodnym ze specyfikacją CLS i zadeklaruj typy. Aby uzyskać pełny opis procesu konwersji importu, zobacz [Podsumowanie konwersji typu Biblioteka na zestaw](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) . Efektywnie, podczas tworzenia niestandardowej OTOKi, ręcznie wykonujesz działanie konwersji typu dostarczone przez [importera biblioteki typów (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md). W przykładzie znajdującym się w następnej sekcji pokazano typy w pliku IDL lub pliku biblioteki typów oraz odpowiadające typy w kodzie języka C#.  
  
3. Gdy deklaracje będą kompletne, skompiluj plik, tak jak kompilujesz dowolny plik z zarządzanym kodem źródłowym.  
  
4. Podobnie jak w przypadku typów importowanych za pomocą narzędzia Tlbimp.exe, niektóre typy wymagają dodatkowych informacji, które możesz dodać bezpośrednio w kodzie. Aby uzyskać szczegółowe informacje [, zobacz How to: Edytuj zestawy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))międzyoperacyjności.  
  
## <a name="example"></a>Przykład  
 W poniższym kodzie pokazano przykład interfejsu `ISATest` i klasy `SATest` napisane w języku IDL oraz odpowiadające typy w kodzie źródłowym języka C#.  
  
 **IDL lub plik biblioteki typów**  
  
```cpp
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

- [Dostosowywanie wywoływanych otok środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))
- [Typy danych COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))
- [Instrukcje: Edytowanie zestawów międzyoperacyjnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))
- [Podsumowanie dotyczące konwersji biblioteki typów na zestaw](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Tlbimp.exe (importer biblioteki typów)](../tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (eksporter biblioteki typów)](../tools/tlbexp-exe-type-library-exporter.md)
