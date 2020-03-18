---
title: -link (Opcje kompilatora C#)
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
ms.openlocfilehash: 4c96f7be5ac500886ea036c93b4651fa814ee58a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970110"
---
# <a name="-link-c-compiler-options"></a>-link (Opcje kompilatora C#)
Powoduje, że kompilator, aby informacje o typie COM w określonych zestawów dostępne dla projektu, który jest obecnie kompilowany.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a>Argumenty  
 `fileList`  
 Wymagany. Lista nazw plików zestawów rozdzielana przecinkami. Jeśli nazwa pliku zawiera spacja, ujmij nazwę w cudzysłów.  
  
## <a name="remarks"></a>Uwagi  
 Ta `-link` opcja umożliwia wdrożenie aplikacji, która ma osadzone informacje o typie. Aplikacja może następnie używać typów w zestawie wykonywania, które implementują informacje o typie osadzonym bez konieczności odwoływania się do zestawu wykonywania. Jeśli zostaną opublikowane różne wersje zestawu w czasie wykonywania, aplikacja zawierająca informacje o typie osadzonym może pracować z różnymi wersjami bez konieczności ponownej kompilacji. Na przykład zobacz [Instruktaż: Osadzanie typów z zestawów zarządzanych](../../../standard/assembly/embed-types-visual-studio.md).  
  
 Korzystanie `-link` z tej opcji jest szczególnie przydatne podczas pracy z com interop. Można osadzać typy COM, tak aby aplikacja nie wymaga już podstawowego zestawu współrzędnego (PIA) na komputerze docelowym. Opcja `-link` instruuje kompilator, aby osadzić informacje o typie COM z zestawu współdziałania, do którego istnieje odwołanie, do wynikowego skompilowany kod. Typ COM jest identyfikowany przez wartość CLSID (GUID). W rezultacie aplikacja może działać na komputerze docelowym, który zainstalował te same typy COM z tymi samymi wartościami IDENTYFIKATORA CLSID. Dobrym przykładem są aplikacje automatyzujące pakiet Microsoft Office. Ponieważ aplikacje, takie jak Office zwykle zachowują tę samą wartość CLSID w różnych wersjach, aplikacja może używać typów COM, do których istnieje odwołanie, o ile na komputerze docelowym jest zainstalowany program .NET Framework 4 lub nowszy, a aplikacja korzysta z metod, właściwości lub zdarzenia, które są uwzględnione w typach COM, do których istnieją odwołania.  
  
 Opcja `-link` osadza tylko interfejsy, struktury i delegatów. Osadzanie klas COM nie jest obsługiwane.  
  
> [!NOTE]
> Podczas tworzenia wystąpienia typu osadzonego COM w kodzie, należy utworzyć wystąpienie przy użyciu odpowiedniego interfejsu. Próba utworzenia wystąpienia typu osadzonego COM przy użyciu coclass powoduje błąd.  
  
 Aby ustawić `-link` opcję w programie Visual Studio, `Embed Interop Types` dodaj odwołanie do zestawu i ustaw właściwość na **true**. Wartością domyślną `Embed Interop Types` dla właściwości jest **false**.  
  
 Jeśli łączysz się z zestawem COM (złożenie M.In.), który sam odwołuje się do innego zestawu COM (zestawu B), należy również połączyć się z zestawem B, jeśli spełniona jest jedna z następujących wartości:  
  
- Typ z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.  
  
- Pole, właściwość, zdarzenie lub metoda, która ma typ zwracany lub typ parametru z zestawu B jest wywoływana.  
  
 Podobnie jak opcja [kompilatora -reference,](./reference-compiler-option.md) opcja `-link` kompilatora używa pliku odpowiedzi Csc.rsp, który odwołuje się do często używanych zestawów .NET Framework. Użyj opcji [kompilatora -noconfig,](./noconfig-compiler-option.md) jeśli nie chcesz, aby kompilator używał pliku Csc.rsp.  
  
 Krótka forma `-link` `-l`jest .  
  
## <a name="generics-and-embedded-types"></a>Typy ogólne i osadzone  
 W poniższych sekcjach opisano ograniczenia dotyczące używania typów ogólnych w aplikacjach, które osadzają typy współotora.  
  
### <a name="generic-interfaces"></a>Interfejsy ogólne  
 Nie można używać interfejsów ogólnych, które są osadzone z zestawu współdziałania. Jest to pokazane w poniższym przykładzie.  
  
 [!code-csharp[VbLinkCompilerCS#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#1)]  
  
### <a name="types-that-have-generic-parameters"></a>Typy, które mają parametry ogólne  
 Typy, które mają parametr ogólny, którego typ jest osadzony z zestawu współdziałania nie może być używany, jeśli ten typ pochodzi z zestawu zewnętrznego. To ograniczenie nie ma zastosowania do interfejsów. Rozważmy na <xref:Microsoft.Office.Interop.Excel.Range> przykład interfejs, który <xref:Microsoft.Office.Interop.Excel> jest zdefiniowany w zestawie. Jeśli biblioteka osadza typy współdziałania z <xref:Microsoft.Office.Interop.Excel> zestawu i udostępnia metodę, która zwraca typ <xref:Microsoft.Office.Interop.Excel.Range> ogólny, który ma parametr, którego typem jest interfejs, ta metoda musi zwrócić ogólny interfejs, jak pokazano w poniższym przykładzie kodu.  
  
 [!code-csharp[VbLinkCompilerCS#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#2)]  
[!code-csharp[VbLinkCompilerCS#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#3)]  
[!code-csharp[VbLinkCompilerCS#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#4)]  
  
 W poniższym przykładzie kod klienta można wywołać metodę, która zwraca <xref:System.Collections.IList> ogólny interfejs bez błędów.  
  
 [!code-csharp[VbLinkCompilerCS#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#5)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `OfficeApp.cs` pliki źródłowe `COMData1.dll` `COMData2.dll` i `OfficeApp.exe`zestawy odwołań z i do produkcji .  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Przewodnik: osadzanie typów z zarządzanych zestawów](../../../standard/assembly/embed-types-visual-studio.md)
- [-reference (Opcje kompilatora C#)](./reference-compiler-option.md)
- [-noconfig (Opcje kompilatora C#)](./noconfig-compiler-option.md)
- [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](./command-line-building-with-csc-exe.md)
- [Przegląd współdziałania](../../programming-guide/interop/interoperability-overview.md)
