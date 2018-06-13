---
title: -link (opcje kompilatora C#)
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
ms.openlocfilehash: 668476beb2eefa7a818f60606443ae06ae26a17d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217210"
---
# <a name="-link-c-compiler-options"></a>-link (opcje kompilatora C#)
Powoduje, że kompilator, aby udostępnić informacje o typie modelu COM w określonych zestawów do projektu, które są aktualnie kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a>Argumenty  
 `fileList`  
 Wymagana. Rozdzielana przecinkami lista nazw plików zestawu. Jeśli nazwa pliku zawiera spację, nazwę należy ująć w cudzysłów.  
  
## <a name="remarks"></a>Uwagi  
 `-link` Opcja umożliwia wdrażanie aplikacji, która zawiera osadzone informacji o typie. Aplikacja może następnie używać typów w zestawie środowiska uruchomieniowego, które implementują informacji osadzonym typem bez konieczności odwołanie do zestawu środowiska wykonawczego. Jeśli w różnych wersjach zestawu środowiska wykonawczego są publikowane, aplikacji, który zawiera informacje o osadzonym typem może współpracować z różnych wersji bez konieczności ponownie skompilowana. Na przykład zobacz [wskazówki: osadzanie typów z zarządzanych zestawów](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).  
  
 Przy użyciu `-link` opcja jest szczególnie przydatne podczas pracy z COM interop. Można osadzić typów COM, aby aplikacja nie wymaga już podstawowy zestaw międzyoperacyjny (PIA) na komputerze docelowym. `-link` Opcja nakazuje kompilatorowi osadzanie informacji o typie COM z przywoływanego zestawu międzyoperacyjnego na wynikowej skompilowanego kodu. Typ modelu COM jest identyfikowany przez wartość identyfikatora CLSID (GUID). W związku z tym aplikację można uruchomić na komputerze docelowym, który zainstalował takich samych typach modelu COM przy użyciu tej samej wartości identyfikatora CLSID. Dobrym przykładem są aplikacje, które automatyzują Microsoft Office. Ponieważ aplikacji, takich jak Office zazwyczaj zachować taką samą wartość identyfikatora CLSID w różnych wersjach, aplikacja może używać wskazanych typów COM, jak długo jako .NET Framework 4 lub nowszy jest zainstalowany na komputerze docelowym i aplikacja korzysta z metod, właściwości lub zdarzenia, które są objęte wskazanych typów COM.  
  
 `-link` Opcja osadza interfejsów, struktur i delegatów. Osadzanie klasy COM nie jest obsługiwane.  
  
> [!NOTE]
>  Podczas tworzenia wystąpienia typu osadzonego modelu COM w kodzie, należy utworzyć wystąpienie przy użyciu odpowiedniego interfejsu. Podjęto próbę utworzenia wystąpienia typu osadzonego modelu COM za pomocą klasy CoClass powoduje błąd.  
  
 Aby ustawić `-link` opcji w programie Visual Studio, Dodaj odwołanie do zestawu danych i ustaw `Embed Interop Types` właściwości **true**. Wartość domyślna dla `Embed Interop Types` właściwość jest **false**.  
  
 Gdy łącze do zestawu COM (zestaw A) które odwołuje się do innego zestawu COM (zestaw B), należy także łącze do zestawu B, jeśli spełniony jest jeden z następujących czynności:  
  
-   Typ z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.  
  
-   Pola, właściwości, zdarzenia lub metodę, która ma zwracany typ lub parametr typu z B zestawu jest wywoływany.  
  
 Podobnie jak [— odwołanie](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) — opcja kompilatora, `-link` — opcja kompilatora używa Csc.rsp plik odpowiedzi, który odwołuje się do często używanych [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów. Użyj [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) opcję kompilatora, jeśli nie chcesz kompilatora, aby użyć pliku Csc.rsp.  
  
 Krótka forma z `-link` jest `-l`.  
  
## <a name="generics-and-embedded-types"></a>Typy ogólne i osadzone typy  
 W poniższych sekcjach opisano ograniczenia przy użyciu typów ogólnych w aplikacjach, które osadzić typów międzyoperacyjnych.  
  
### <a name="generic-interfaces"></a>Interfejsy ogólne  
 Nie można używać interfejsów ogólnych osadzonych z zestawu międzyoperacyjnego. Przedstawiono to w poniższym przykładzie.  
  
 [!code-csharp[VbLinkCompilerCS#1](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_1.cs)]  
  
### <a name="types-that-have-generic-parameters"></a>Typy, które mają parametry ogólne  
 Typy, które mają parametru ogólnego, którego typ jest osadzony z zestawu międzyoperacyjnego nie można użyć Jeśli typ jest z zewnętrznego zestawu. To ograniczenie nie ma zastosowania do interfejsów. Rozważmy na przykład <xref:Microsoft.Office.Interop.Excel.Range> interfejs, który jest zdefiniowany w <xref:Microsoft.Office.Interop.Excel> zestawu. Jeśli biblioteki osadza typów międzyoperacyjnych z <xref:Microsoft.Office.Interop.Excel> zestawu i udostępnia metodę, która zwraca wartość typu ogólnego, który ma parametr typu jest <xref:Microsoft.Office.Interop.Excel.Range> interfejsu, metoda musi zwracać interfejs ogólny, jak pokazano w poniższym przykładzie kodu.  
  
 [!code-csharp[VbLinkCompilerCS#2](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_2.cs)]  
[!code-csharp[VbLinkCompilerCS#3](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_3.cs)]  
[!code-csharp[VbLinkCompilerCS#4](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_4.cs)]  
  
 W poniższym przykładzie kodu klienta można wywołać metodę, która zwraca <xref:System.Collections.IList> ogólny interfejs bez błędów.  
  
 [!code-csharp[VbLinkCompilerCS#5](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_5.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy plik źródłowy `OfficeApp.cs` i odwołuje się do zestawów z `COMData1.dll` i `COMData2.dll` do produkcji `OfficeApp.exe`.  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Przewodnik: osadzanie typów z zarządzanych zestawów](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [— Odwołanie (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)  
 [-noconfig (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)  
 [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [Przegląd współdziałania](../../../csharp/programming-guide/interop/interoperability-overview.md)
