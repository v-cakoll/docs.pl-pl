---
title: 'Porady: wyświetlanie zawartości zestawu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eadc320483d46503e7331ef57b0cc29b08f13f4c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-view-assembly-contents"></a>Porady: wyświetlanie zawartości zestawu
Można użyć [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) Aby wyświetlić informacje o języku pośrednim (MSIL) firmy Microsoft w pliku. Jeśli badane plik jest zestawem, te informacje mogą uwzględniać zestaw atrybutów, a także odwołania do innych modułów i zestawów. Informacje te mogą być pomocne w określeniu, czy plik jest zestawem lub część zestawu i określa, czy plik ma odwołania do innych modułach ani zestawów.  
  
### <a name="to-display-the-contents-of-an-assembly-using-ildasmexe"></a>Aby wyświetlić zawartość zestawu za pomocą Ildasm.exe  
  
1.  Typ **narzędzia ildasm** \< *nazwy zestawu*> w wierszu polecenia. Na przykład następujące polecenie rozkłada `Hello.exe` zestawu.  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### <a name="to-view-assembly-manifest-information"></a>Aby wyświetlić informacje manifestu zestawu  
  
1.  Kliknij dwukrotnie ikonę MANIFESTU w oknie dezasembler MSIL.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rozpoczyna się od podstawowego program "Hello, World". Po kompilacji programu, należy użyć Ildasm.exe dezasemblować zestawu Hello.exe i wyświetlania manifest zestawu.  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 Uruchamiając polecenie ildasm.exe na zestawu Hello.exe i dwukrotne kliknięcie ikony MANIFESTU w oknie IL DASM tworzy następujące dane wyjściowe:  
  
```  
// Metadata version: v4.0.30319  
.assembly extern mscorlib  
{  
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..  
  .ver 4:0:0:0  
}  
.assembly Hello  
{  
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )   
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx  
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.  
  .hash algorithm 0x00008004  
  .ver 0:0:0:0  
}  
.module Hello.exe  
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}  
.imagebase 0x00400000  
.file alignment 0x00000200  
.stackreserve 0x00100000  
.subsystem 0x0003       // WINDOWS_CUI  
.corflags 0x00000001    //  ILONLY  
// Image base: 0x00600000  
```  
  
 W poniższej tabeli opisano każdy dyrektywy w manifeście zestawu zestawu Hello.exe używane w przykładzie.  
  
|Dyrektywy|Opis|  
|---------------|-----------------|  
|**Deklaracja extern \<**  *nazwy zestawu* **>**|Określa innego zestawu, który zawiera elementy, które odwołuje się moduł bieżący (w tym przykładzie `mscorlib`).|  
|**.PublicKeyToken \<**  *tokenu* **>**|Określa token klucza rzeczywiste przywoływanego zestawu.|  
|**.ver \<**  *numer wersji* **>**|Określa numer wersji przywoływanego zestawu.|  
|**Deklaracja \<**  *nazwy zestawu* **>**|Określa nazwę zestawu.|  
|**algorytm .hash \<**  *wartość int32* **>**|Określa algorytm wyznaczania wartości skrótu używany.|  
|**.ver \<**  *numer wersji* **>**|Określa numer wersji zestawu.|  
|**.module \<**  *nazwy pliku* **>**|Określa nazwę modułów, które tworzą zestaw. W tym przykładzie zestaw składa się z tylko jednego pliku.|  
|**.Subsystem \<**  *wartości* **>**|Określa środowisko aplikacji wymagane przez program. W tym przykładzie wartość 3 oznacza, że ten plik wykonywalny jest uruchamiane z poziomu konsoli.|  
|**.corflags**|Obecnie zastrzeżone pole w metadanych.|  
  
 Manifest zestawu może zawierać wiele różnych dyrektyw, w zależności od zestawu zawartości. Obszernej listy dyrektywy w manifeście zestawu dokumentacji ECMA, szczególnie "Partycji II: metadane definicji i semantyki" i "III: CIL instrukcji zestawu partycji". Dokumentacja jest dostępna w trybie online; zobacz [ECMA C# i wspólne normy infrastruktury języka](http://go.microsoft.com/fwlink/?LinkID=99212) w witrynie MSDN i [standardowe ECMA-335 - infrastruktury języka wspólnego (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) w witrynie sieci Web międzynarodowej Ecma.  
  
## <a name="see-also"></a>Zobacz też  
 [Domeny aplikacji i zestawy](http://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)  
 [Instrukcje dotyczące zestawów i domen aplikacji](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
