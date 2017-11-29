---
title: Kompilator XSLT (xsltc.exe)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2b4ede7bdb8dad65e9cd959dfaa2f8956a877762
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xslt-compiler-xsltcexe"></a>Kompilator XSLT (xsltc.exe)
Kompilator XSLT (xsltc.exe) kompiluje arkuszy stylów XSLT i generuje zestawu. Arkusz stylów skompilowanego można następnie przekazać bezpośrednio do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metody. Nie można wygenerować zestawy podpisane za pomocą xsltc.exe.  
  
 Narzędzie xsltc.exe jest dołączone do programu Visual Studio 2008. Aby uzyskać więcej informacji, zobacz [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=89463).  
  
## <a name="syntax"></a>Składnia  
  
```  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a>Argument  
  
|Argument|Opis|  
|--------------|-----------------|  
|`sourceFile`|Określa nazwę arkusza stylów. Arkusz stylów musi być lokalny plik lub znajdować się w intranecie.|  
  
## <a name="options"></a>Opcje  
  
|Opcja|Opis|  
|------------|-----------------|  
|`/c[lass]:``name`|Określa nazwę klasy dla następujących arkusza stylów. Nazwa klasy może być w pełni kwalifikowana.<br /><br /> Nazwa klasy domyślnie nazwa arkusza stylów. Na przykład jeśli customers.xsl arkusza stylów jest skompilowany, domyślną nazwę klasy jest klientów.|  
|`/debug[`+&#124;-`]`|Określa, czy generować informacji o debugowaniu.<br /><br /> Określanie `+` lub `/debug`, powoduje, że kompilator generuje informacje o debugowaniu i umieszcza je w plik programu (PDB) bazy danych. Nazwa pliku PDB wygenerowanego jest `assemblyName`.pdb.<br /><br /> Określanie `-`, która jest włączona, jeśli nie określisz `/debug`, powoduje, że żadne informacje o debugowaniu ma zostać utworzony. Generowany jest zestawem sprzedaży detalicznej. **Uwaga:** kompilowanie w trybie debugowania mogą wpływać na wydajność XSLT w znacznym stopniu.|  
|`/help`|Wyświetla składnię polecenia i opcje narzędzia.|  
|`/nologo`|Pomija komunikat o prawach autorskich kompilatora przy wyświetlaniu.|  
|`/platform:``string`|Określa platformy, które można uruchomić zestawu na. Poniżej opisano platformy prawidłowe wartości:<br /><br /> `x86`kompiluje z zestawu do uruchomienia przez 32-bitowy, x86 zgodnego wykonywalnych języka wspólnego<br /><br /> `x64`kompiluje z zestawu do uruchomienia na komputerze, który obsługuje zestaw instrukcji AMD64 lub EM64T przez 64-bitowe środowisko uruchomieniowe języka wspólnego.<br /><br /> [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)]kompiluje z zestawu do uruchomienia w 64-bitowego środowiska CLR na komputerze, który ma [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)] procesora.<br /><br /> `anycpu`kompiluje używanemu zestawowi można uruchomić na dowolnej platformie. Domyślnie włączone.|  
|`/out:``assemblyName`|Określa nazwę zestawu, który jest danych wyjściowych. Nazwy zestawu domyślnie nazwę arkusza stylów głównego lub pierwszego arkusza stylów, jeśli istnieją arkuszy stylów.<br /><br /> Jeśli arkusz stylów zawiera skryptów, skrypty są zapisywane osobny zestaw. Nazw zestawów skryptu są generowane na podstawie nazwy zestawu głównego. Na przykład jeśli określono CustOrders.dll nazwy zestawu, pierwszy zestaw skryptu nosi nazwę CustOrders_Script1.dll.|  
|`/settings:``document+-, script+-, DTD+-,`|Określa, czy zezwalać `document()` funkcje, skrypt XSLT lub dokument definicji (DTD) należy wpisać w arkuszu stylów.<br /><br /> Domyślnie wyłącza obsługę definicji DTD, `document()` funkcji i skryptów.|  
|`@``file`|Pozwala określić plik, który zawiera opcje kompilatora.|  
|`?`|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Rozwiązania XSLT może obejmować wiele modułów arkusza stylów. Narzędzie xsltc.exe generuje zestawy z arkuszy stylów. Zestawy można następnie przekazać do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metody. Może to ułatwić zmniejszenie kosztów wydajności w niektórych scenariuszach wdrażania XSLT.  
  
> [!NOTE]
>  Należy również uwzględnić skompilowanego zestawu jako odwołania w aplikacji.  
  
 Narzędzie xsltc.exe nie można zweryfikować klasy (`/class:``name`) lub zestawu (`/out:``assemblyName`) nazwy. Błędy zwracane przez środowisko uruchomieniowe języka wspólnego Jeśli nazwy nie są prawidłowe.  
  
## <a name="examples"></a>Przykłady  
 Poniższe polecenie kompiluje arkusza stylów i tworzy zestaw o nazwie booksort.dll.  
  
```  
xsltc booksort.xsl  
```  
  
 Poniższe polecenie kompiluje arkusza stylów i powoduje utworzenie zestawu i pliku PDB, które są nazywane booksort.dll i booksort.pdb odpowiednio.  
  
```  
xsltc booksort.xsl /debug  
```  
  
 Poniższe polecenie kompiluje arkusza stylów, który zawiera msxsl:script element i utworzenie dwóch zestawów o nazwie calc.dll i calc_Script1.dll.  
  
```  
xsltc /settings:script+ calc.xsl  
```  
  
 Poniższe polecenie umożliwia obsługę definicji DTD przetwarzania i skryptów i tworzy dwóch zestawów o nazwie myTest.dll i myTest_Script1.dll.  
  
```  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 Poniższe polecenie kompiluje dwa moduły arkusza stylów i tworzy jednym zestawie o nazwie booksort.dll.  
  
```  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [Porady: przekształcenie XSLT przy użyciu zestawu](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)  
 [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
