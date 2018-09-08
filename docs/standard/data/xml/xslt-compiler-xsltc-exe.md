---
title: Kompilator XSLT (xsltc.exe)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 470dd0eb37d8081d388ef69b204293f568096a5e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197556"
---
# <a name="xslt-compiler-xsltcexe"></a>Kompilator XSLT (xsltc.exe)
Kompilator XSLT (xsltc.exe) kompiluje arkuszy stylów XSLT i generuje zestaw. Arkusz stylów skompilowanego można następnie przekazać bezpośrednio do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metody. Nie można wygenerować zestawy podpisane za pomocą xsltc.exe.  
  
 Narzędzie xsltc.exe jest dołączony do Visual Studio. Aby uzyskać więcej informacji, zobacz [pobieranie Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).  
  
## <a name="syntax"></a>Składnia  
  
```  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a>Argument  
  
|Argument|Opis|  
|--------------|-----------------|  
|`sourceFile`|Określa nazwę arkusza stylów. Arkusz stylów musi być plikiem lokalnym lub znajdować się w sieci intranet.|  
  
## <a name="options"></a>Opcje  
  
|Opcja|Opis|  
|------------|-----------------|  
|`/c[lass]:``name`|Określa nazwę klasy następujące arkusza stylów. Nazwa klasy może być w pełni kwalifikowana.<br /><br /> Nazwa klasy jest wartością domyślną nazwę arkusza stylów. Na przykład jeśli customers.xsl arkusza stylów jest kompilowany, domyślną nazwę klasy jest klientów.|  
|`/debug[`+&#124;-`]`|Określa, czy informacje debugowania będą generowane.<br /><br /> Określanie `+` lub `/debug`, powoduje, że kompilator generuje informacje o debugowaniu i umieszcza je w pliku bazy danych (PDB) programu. Nazwę wygenerowanego pliku PDB jest `assemblyName`.pdb.<br /><br /> Określanie `-`, ponieważ jest aktywna, jeśli nie określisz `/debug`, powoduje, że żadne informacje debugowania do utworzenia. Zestaw danych sprzedaży detalicznej jest generowany. **Uwaga:** kompilowanie w trybie debugowania może wpłynąć na wydajność XSLT w znacznym stopniu.|  
|`/help`|Wyświetla składnię polecenia i opcje narzędzia.|  
|`/nologo`|Pomija komunikat o prawach autorskich kompilatora były wyświetlane.|  
|`/platform:``string`|Określa platform, które zestawu mogą być uruchamiane na. Poniżej opisano platformy prawidłowe wartości:<br /><br /> `x86` kompiluje zestaw do uruchomienia w 32-bitowy, x86 zgodne środowisko uruchomieniowe języka wspólnego<br /><br /> `x64` kompiluje zestaw do uruchomienia na komputerze, który obsługuje zestaw instrukcji AMD64 lub EM64T przez 64-bitowe środowisko uruchomieniowe języka wspólnego.<br /><br /> [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] kompiluje zestaw do uruchomienia w 64-bitowe środowisko uruchomieniowe języka wspólnego na komputerze, który ma [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] procesora.<br /><br /> `anycpu` Kompiluje zestaw można uruchomić na dowolnej platformie. Domyślnie włączone.|  
|`/out:``assemblyName`|Określa nazwę zestawu, który jest dane wyjściowe. Nazwa zestawu wartość domyślna to nazwę arkusza stylów głównego lub pierwszego arkusza stylów, jeśli podano wiele arkuszy stylów.<br /><br /> Jeśli arkusz stylów zawiera skryptów, skrypty są zapisywane w osobnym zestawie. Nazwy zestawów skryptu są generowane na podstawie nazwy zestawu głównego. Na przykład jeśli określono CustOrders.dll dla nazwy zestawu, pierwszy zestaw skryptów nosi nazwę CustOrders_Script1.dll.|  
|`/settings:``document+-, script+-, DTD+-,`|Określa, czy zezwalać na `document()` funkcji, skryptu XSLT lub dokumencie wpisz definicję (DTD) w arkuszu stylów.<br /><br /> Domyślne zachowanie wyłącza obsługę definicji DTD, `document()` funkcji i skryptów.|  
|`@``file`|Pozwala określić plik, który zawiera opcje kompilatora.|  
|`?`|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Rozwiązania XSLT może obejmować wiele modułów arkusza stylów. Narzędzie xsltc.exe generująca zestawy z arkuszy stylów. Zestawy mogą być następnie przekazywany do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metody. Pozwoli to zmniejszyć koszty wydajności w niektórych scenariuszach wdrażania XSLT.  
  
> [!NOTE]
>  Należy również uwzględnić skompilowanego zestawu jako odwołania w aplikacji.  
  
 Narzędzie xsltc.exe nie można zweryfikować klasy (`/class:``name`) lub zestawu (`/out:``assemblyName`) nazwy. Błędy są zgłaszane przez środowisko uruchomieniowe języka wspólnego, jeśli nazwy nie są prawidłowe.  
  
## <a name="examples"></a>Przykłady  
 Poniższe polecenie kompiluje arkusza stylów i tworzy zestaw o nazwie booksort.dll.  
  
```  
xsltc booksort.xsl  
```  
  
 Poniższe polecenie kompiluje arkusza stylów i powoduje utworzenie zestawu i pliku PDB, które są nazywane booksort.dll i booksort.pdb odpowiednio.  
  
```  
xsltc booksort.xsl /debug  
```  
  
 Poniższe polecenie kompiluje arkusza stylów, który zawiera element msxsl: Script i tworzy dwa zestawy o nazwie calc.dll i calc_Script1.dll.  
  
```  
xsltc /settings:script+ calc.xsl  
```  
  
 Następujące polecenie umożliwia obsługę skryptów i przetwarzania DTD i tworzy dwa zestawy o nazwie myTest.dll i myTest_Script1.dll.  
  
```  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 Poniższe polecenie kompiluje dwa moduły arkusza stylów i tworzy pojedynczy zestaw o nazwie booksort.dll.  
  
```  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Xsl.XslCompiledTransform>  
- [Instrukcje: Wykonywanie przekształcenia XSLT przy użyciu zestawu](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)  
- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
