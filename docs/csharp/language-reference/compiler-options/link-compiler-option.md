---
title: -Link (C# opcje kompilatora)
ms.date: 07/20/2015
helpviewer_keywords:
- /l compiler option [C#]
- /link compiler option [C#]
- -l compiler option [C#]
- EmbedInteropTypes
- l compiler option [C#]
- embed interop types [COM Interop]
- -link compiler option [C#]
- link compiler option [C#]
ms.assetid: 00da70c6-9ea1-43c2-86f2-aa7f26c03475
ms.openlocfilehash: 724a848d4c31b2c4f6fc3427d70fc84f4fd944c6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924759"
---
# <a name="-link-c-compiler-options"></a>-Link (C# opcje kompilatora)
Powoduje, że kompilator udostępnia informacje o typie COM w określonych zestawach, które są dostępne dla aktualnie kompilowanego projektu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a>Argumenty  
 `fileList`  
 Wymagany. Rozdzielana przecinkami lista nazw plików zestawu. Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów.  
  
## <a name="remarks"></a>Uwagi  
 `-link` Opcja umożliwia wdrożenie aplikacji, która ma informacje o typie osadzonym. Aplikacja może następnie użyć typów w zestawie środowiska uruchomieniowego, który implementuje informacje o typie osadzonym, bez konieczności odwoływania się do zestawu środowiska uruchomieniowego. Jeśli są publikowane różne wersje zestawu środowiska uruchomieniowego, aplikacja zawierająca informacje o typie osadzonym może współdziałać z różnymi wersjami bez konieczności ponownego kompilowania. Aby zapoznać się z przykładem, zobacz [Przewodnik: Osadzanie typów z zarządzanych zestawów](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).  
  
 Korzystanie z `-link` tej opcji jest szczególnie przydatne podczas pracy z międzyoperacyjnym modelem com. Można osadzić typy COM, aby aplikacja nie wymagała już podstawowego zestawu międzyoperacyjnego (PIA) na komputerze docelowym. `-link` Opcja instruuje kompilator, aby osadzi informacje o typie com z przywoływanego zestawu międzyoperacyjnego do w wyniku skompilowanego kodu. Typ COM jest identyfikowany przez wartość CLSID (GUID). W związku z tym aplikacja może działać na komputerze docelowym, na którym zainstalowano te same typy COM z tymi samymi wartościami CLSID. Aplikacje automatyzujące Microsoft Office są dobrym przykładem. Ponieważ aplikacje takie jak pakiet Office zwykle zachowują tę samą wartość CLSID w różnych wersjach, aplikacja może używać typów COM, których dotyczy odwołanie, tak długo, jak .NET Framework 4 lub nowszy jest zainstalowany na komputerze docelowym, a aplikacja korzysta z metod, właściwości lub zdarzenia, które są zawarte w przywoływanych typach COM.  
  
 `-link` Opcja osadza tylko interfejsy, struktury i delegatów. Osadzanie klas COM nie jest obsługiwane.  
  
> [!NOTE]
> Podczas tworzenia wystąpienia osadzonego typu COM w kodzie, należy utworzyć wystąpienie przy użyciu odpowiedniego interfejsu. Próba utworzenia wystąpienia osadzonego typu COM przy użyciu klasy coclass powoduje wystąpienie błędu.  
  
 Aby ustawić `-link` opcję w programie Visual Studio, Dodaj odwołanie do zestawu i `Embed Interop Types` ustaw właściwość na **wartość true**. Wartość domyślna dla `Embed Interop Types` właściwości ma **wartość false**.  
  
 Jeśli utworzysz link do zestawu COM (zestawu A), który sam odwołuje się do innego zestawu COM (zestawu B), musisz także połączyć się z zestawem B, jeśli jest spełniony jeden z następujących warunków:  
  
- Typ z zestawu A dziedziczy po typie lub implementuje interfejs z zestawu B.  
  
- Wywołano pole, właściwość, zdarzenie lub metodę z typem zwracanym lub typem parametru z zestawu B.  
  
 Podobnie jak w przypadku opcji kompilatora [odwołania](./reference-compiler-option.md) , `-link` opcja kompilatora używa pliku odpowiedzi CSC. rsp, który odwołuje się do często używanych zestawów .NET Framework. Użyj opcji kompilatora [-noconfig](./noconfig-compiler-option.md) , jeśli nie chcesz, aby kompilator używał pliku CSC. rsp.  
  
 Krótka forma `-link` to `-l`.  
  
## <a name="generics-and-embedded-types"></a>Typy ogólne i osadzone  
 W poniższych sekcjach opisano ograniczenia dotyczące używania typów ogólnych w aplikacjach, które osadzają typy międzyoperacyjnych.  
  
### <a name="generic-interfaces"></a>Interfejsy ogólne  
 Nie można użyć ogólnych interfejsów, które są osadzone z zestawu międzyoperacyjnego. Pokazano to w poniższym przykładzie.  
  
 [!code-csharp[VbLinkCompilerCS#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#1)]  
  
### <a name="types-that-have-generic-parameters"></a>Typy, które mają parametry ogólne  
 Typów, które mają parametr generyczny, którego typ jest osadzony z zestawu międzyoperacyjnego nie można użyć, jeśli ten typ pochodzi z zewnętrznego zestawu. To ograniczenie nie ma zastosowania do interfejsów. Rozważmy <xref:Microsoft.Office.Interop.Excel.Range> na przykład interfejs, który jest zdefiniowany <xref:Microsoft.Office.Interop.Excel> w zestawie. Jeśli biblioteka osadza typy międzyoperacyjnych z <xref:Microsoft.Office.Interop.Excel> zestawu i uwidacznia metodę, która zwraca typ ogólny, który ma parametr, którego typem <xref:Microsoft.Office.Interop.Excel.Range> jest interfejs, ta metoda musi zwracać interfejs ogólny, jak pokazano w poniższym przykładzie kodu.  
  
 [!code-csharp[VbLinkCompilerCS#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#2)]  
[!code-csharp[VbLinkCompilerCS#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#3)]  
[!code-csharp[VbLinkCompilerCS#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#4)]  
  
 W poniższym przykładzie kod klienta może wywołać metodę, która zwraca <xref:System.Collections.IList> interfejs generyczny bez błędu.  
  
 [!code-csharp[VbLinkCompilerCS#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#5)]  
  
## <a name="example"></a>Przykład  
 Poniższy `OfficeApp.cs` kod kompiluje pliki źródłowe i zestawy odwołań z `COMData1.dll` i `COMData2.dll` do produkcji. `OfficeApp.exe`  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Przewodnik: Osadzanie typów z zarządzanych zestawów](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [-Reference (C# opcje kompilatora)](./reference-compiler-option.md)
- [-noconfig (C# opcje kompilatora)](./noconfig-compiler-option.md)
- [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](./command-line-building-with-csc-exe.md)
- [Przegląd współdziałania](../../programming-guide/interop/interoperability-overview.md)
