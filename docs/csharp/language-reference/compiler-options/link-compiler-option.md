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
ms.openlocfilehash: 00cfda489feb468c7e3c140ab63369b408b09152
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44183252"
---
# <a name="-link-c-compiler-options"></a>-link (opcje kompilatora C#)
Powoduje, że kompilator udostępnia informacje o typie modelu COM w określonych zestawach do projektu, który obecnie kompilacja.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a>Argumenty  
 `fileList`  
 Wymagane. Rozdzielana przecinkami lista nazw plików zestawu. Jeśli nazwa pliku zawiera spację, nazwę należy ująć w znaki cudzysłowu.  
  
## <a name="remarks"></a>Uwagi  
 `-link` Opcja służy do wdrażania aplikacji, która zawiera osadzone informacje o typie. Aplikacja następnie można użyć typów w zestawie środowiska uruchomieniowego, które implementują informacje o typie osadzony bez odwołania do zestawu środowiska wykonawczego. Jeśli różne wersje zestawów środowiska uruchomieniowego są publikowane, aplikacji, która zawiera informacje o typie osadzony pracować z różnymi wersjami bez konieczności zostać zrekompilowane. Aby uzyskać przykład, zobacz [wskazówki: osadzanie typów z zarządzanych zestawów](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).  
  
 Za pomocą `-link` opcja jest szczególnie przydatna w przypadku, gdy pracujesz za pomocą modelu COM. Można osadzić typów modelu COM, dzięki czemu aplikacja nie wymaga już podstawowego zestawu międzyoperacyjnego (PIA) na komputerze docelowym. `-link` Opcja nakazuje kompilatorowi osadzanie informacji o typie modelu COM z odwołania zestawu międzyoperacyjnego wynikowy kod skompilowany. Typ COM jest identyfikowany przez wartość identyfikatora CLSID (GUID). W rezultacie aplikację można uruchomić na komputerze docelowym, w której zainstalowano te same typy modelu COM za pomocą tych samych wartości identyfikatora CLSID. Aplikacje, które automatyzują Microsoft Office są dobrym przykładem. Ponieważ aplikacji, takich jak Office zwykle zachować tę samą wartość identyfikatora CLSID różnych wersji, aplikacja może używać typów modelu COM, jak długo, jak .NET Framework 4 lub nowszy jest zainstalowany na komputerze docelowym, a Twoja aplikacja używa metod, właściwości lub zdarzenia, które są zawarte w przywoływanych typów modelu COM.  
  
 `-link` Opcja osadza interfejsy, struktury i delegatów. Osadzanie klasy COM nie jest obsługiwane.  
  
> [!NOTE]
>  Podczas tworzenia wystąpienia typu osadzonego modelu COM w kodzie, należy utworzyć wystąpienie przy użyciu odpowiedniego interfejsu. Próba utworzenia wystąpienia typu osadzonego modelu COM za pomocą wspólna spowoduje wystąpienie błędu.  
  
 Aby ustawić `-link` opcji w programie Visual Studio, Dodaj odwołanie do zestawu i ustaw `Embed Interop Types` właściwości **true**. Wartość domyślna dla `Embed Interop Types` właściwość **false**.  
  
 Jeśli łączysz się do zestawu COM (Assembly A) która sama odwołuje się do innego zestawu modelu COM (Assembly B), musisz również link do zestawu B, jeśli jest spełniony jeden z następujących czynności:  
  
-   Typ z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.  
  
-   Pola, właściwości, zdarzenia lub metody, która ma typ lub parametr typu zwracanego z zestawu B zostanie wywołana.  
  
 Podobnie jak [— odwołanie](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) — opcja kompilatora, `-link` — opcja kompilatora korzysta z pliku odpowiedzi Csc.rsp odwołania często używane [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów. Użyj [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) opcji kompilatora, jeśli nie chcesz, aby kompilator, aby użyć pliku Csc.rsp.  
  
 Krótkiej formy `-link` jest `-l`.  
  
## <a name="generics-and-embedded-types"></a>Typy ogólne i osadzone typy  
 W poniższych sekcjach opisano ograniczenia dotyczące używania typów ogólnych w aplikacjach, które osadzić typów międzyoperacyjnych.  
  
### <a name="generic-interfaces"></a>Interfejsy ogólne  
 Nie można używać interfejsów ogólnych, które są osadzone w zestaw międzyoperacyjny. Jest to pokazane w poniższym przykładzie.  
  
 [!code-csharp[VbLinkCompilerCS#1](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_1.cs)]  
  
### <a name="types-that-have-generic-parameters"></a>Typy, które mają parametry ogólne  
 Typy, które mają parametr ogólny, którego typ jest osadzony z zestawu międzyoperacyjnego nie można użyć Jeśli typ jest z zestawu zewnętrznego. To ograniczenie nie ma zastosowania do interfejsów. Na przykład, rozważmy <xref:Microsoft.Office.Interop.Excel.Range> interfejsu, który jest zdefiniowany w <xref:Microsoft.Office.Interop.Excel> zestawu. Jeśli biblioteka osadza typów międzyoperacyjnych z <xref:Microsoft.Office.Interop.Excel> zestawu i udostępnia metodę, która zwraca typ ogólny, który ma parametr, którego typ jest <xref:Microsoft.Office.Interop.Excel.Range> interfejsu i metoda musi zwracać interfejs ogólny, jak pokazano w poniższym przykładzie kodu.  
  
 [!code-csharp[VbLinkCompilerCS#2](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_2.cs)]  
[!code-csharp[VbLinkCompilerCS#3](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_3.cs)]  
[!code-csharp[VbLinkCompilerCS#4](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_4.cs)]  
  
 W poniższym przykładzie, kod klienta może wywołać metodę, która zwraca <xref:System.Collections.IList> interfejs ogólny bez błędów.  
  
 [!code-csharp[VbLinkCompilerCS#5](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_5.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje plik źródłowy `OfficeApp.cs` i odwoływać się do zestawów z `COMData1.dll` i `COMData2.dll` do produkcji `OfficeApp.exe`.  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Przewodnik: osadzanie typów z zarządzanych zestawów](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
- [— Odwołanie (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)  
- [-noconfig (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)  
- [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
- [Przegląd współdziałania](../../../csharp/programming-guide/interop/interoperability-overview.md)
