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
ms.openlocfilehash: abe4c130fb5da49ed0f53c776e23dba8fb5b15f7
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46480607"
---
# <a name="how-to-view-assembly-contents"></a>Porady: wyświetlanie zawartości zestawu
Możesz użyć [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) Aby wyświetlić informacje o Microsoft intermediate language (MSIL) w pliku. Jeśli plik sprawdzane jest zestawem, te informacje mogą obejmować zestawu atrybutów, a także odwołania do innych modułach i zestawach. Te informacje mogą być pomocne w określeniu, czy plik jest zestaw lub częścią zespołu i tego, czy plik ma odwołania do innych modułów lub zestawów.  
  
### <a name="to-display-the-contents-of-an-assembly-using-ildasmexe"></a>Aby wyświetlić zawartość zestawu przy użyciu Ildasm.exe  
  
1.  Typ **ildasm** \< *nazwy zestawu*> w tym celu w wierszu polecenia. Na przykład następujące polecenie dezasembluje `Hello.exe` zestawu.  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### <a name="to-view-assembly-manifest-information"></a>Aby wyświetlić dane manifestu zestawu  
  
1.  Kliknij ikonę MANIFESTU w oknie dezasembler MSIL.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rozpoczyna się od podstawowych programu "Hello, World". Po kompilacji program, należy użyć Ildasm.exe dezasemblować zestawu Hello.exe i wyświetlić manifest zestawu.  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 Uruchomiony ildasm.exe polecenia w zestawie Hello.exe, a następnie dwukrotne kliknięcie ikony MANIFESTU w oknie IL DASM generuje następujące wyniki:  
  
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
  
 W poniższej tabeli opisano każdy dyrektywy w manifeście zestawu zestawu Hello.exe użytych w przykładzie.  
  
|— Dyrektywa|Opis|  
|---------------|-----------------|  
|**Deklaracja extern \<**  *nazwy zestawu* **>**|Określa innego zestawu, który zawiera elementy, które odwołuje się moduł bieżący (w tym przykładzie `mscorlib`).|  
|**.PublicKeyToken \<**  *tokenu* **>**|Określa token rzeczywistego klucza przywoływanego zestawu.|  
|**.ver \<**  *numer wersji* **>**|Określa numer wersji przywoływanego zestawu.|  
|**Deklaracja \<**  *nazwy zestawu* **>**|Określa nazwę zestawu.|  
|**algorytm .hash \<**  *wartość int32* **>**|Określa algorytm wyznaczania wartości skrótu.|  
|**.ver \<**  *numer wersji* **>**|Określa numer wersji zestawu.|  
|**.module \<**  *nazwy pliku* **>**|Określa nazwę moduły, które tworzą zestaw. W tym przykładzie zestaw składa się tylko jeden plik.|  
|**.Subsystem \<**  *wartość* **>**|Określa środowisko aplikacji wymagane przez program. W tym przykładzie wartość 3 wskazuje, że ten plik wykonywalny jest uruchamiany z poziomu konsoli.|  
|**.corflags**|Obecnie zastrzeżone polem w metadanych.|  
  
 Manifest zestawu może zawierać wiele różnych dyrektyw, w zależności od zawartości zestawu. Aby obszerną listę dyrektyw w manifeście zestawu zobacz dokumentację ECMA, szczególnie "Partycja II: metadane definicji i semantyka" oraz "Partition III: CIL instrukcji Set". Dokumentacja jest dostępna w trybie online; zobacz [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) w witrynie MSDN i [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) w witrynie Ecma International w sieci Web.  
  
## <a name="see-also"></a>Zobacz też  
 [Domeny aplikacji i zestawy](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)  
 [Instrukcje dotyczące zestawów i domen aplikacji](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
