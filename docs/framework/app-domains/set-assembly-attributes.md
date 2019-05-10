---
title: Ustawienie atrybutów zestawu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 638ea8c1f01c62075fc4399cada282128e07422d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607546"
---
# <a name="setting-assembly-attributes"></a>Ustawienie atrybutów zestawu
Atrybuty zestawu są wartości, które dostarczają informacje o zestawie. Atrybuty są podzielone na następujące rodzaje informacji:  
  
- Atrybuty tożsamości zestawu.  
  
- Atrybuty informacyjne.  
  
- Atrybuty manifestu zestawu.  
  
- Atrybuty silnej nazwy.  
  
## <a name="assembly-identity-attributes"></a>Atrybuty tożsamości zestawu  
 Trzy atrybuty, wraz z nazwą silną (jeśli dotyczy), określają tożsamość zestawu: nazwę, wersję i kulturę. Te atrybuty tworzą pełną nazwę zestawu i są wymagane, gdy odwołanie do zestawu w kodzie. Atrybuty można użyć, można ustawić wersję i kulturę zestawu. Kompilator lub [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) ustawia wartość nazwy, gdy zestaw jest tworzony na podstawie pliku zawierającego manifest zestawu.  
  
 W poniższej tabeli opisano atrybuty wersję i kulturę.  
  
|Atrybut tożsamości zestawu|Opis|  
|---------------------------------|-----------------|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Pole wyliczany wskazujący kultury, który obsługuje zestaw. Zestaw można również określić niezależność od kultury, wskazującą, czy zawiera on zasobów dla kultury domyślnej. **Uwaga:**  Środowisko uruchomieniowe traktuje zestawu, który ma atrybut kultury ustawiony na wartość null jako zestawu satelickiego. Takie zestawy podlegają zasad powiązania zestawu satelickiego. Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Wartość, która ustawia atrybutów zestawu, na przykład tego, czy zestaw można uruchomić równolegle.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Wartość liczbową w formacie *głównych*. *drobne*. *Tworzenie*. *poprawka* (na przykład 2.4.0.0). Środowisko uruchomieniowe języka wspólnego używa tej wartości do wykonywania operacji wiązania w zestawach o silnej nazwie. **Uwaga:**  Jeśli <xref:System.Reflection.AssemblyInformationalVersionAttribute> atrybut nie ma zastosowania do zestawu, numer wersji określony przez <xref:System.Reflection.AssemblyVersionAttribute> atrybut jest używany przez <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>, i <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> właściwości.|  
  
 Poniższy przykład kodu pokazuje sposób stosowania atrybutów wersję i kulturę do zestawu.  
  
 [!code-cpp[AssemblyDelaySignAttribute#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#3)]
 [!code-csharp[AssemblyDelaySignAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#3)]
 [!code-vb[AssemblyDelaySignAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#3)]  
  
## <a name="informational-attributes"></a>Atrybuty informacyjne  
 Aby zapewnić dodatkowe firmy lub informacje o produkcie dla zestawu, można użyć atrybuty informacyjne. W poniższej tabeli opisano atrybuty informacyjne, które można zastosować do zestawu.  
  
|Atrybut informacyjne|Opis|  
|-----------------------------|-----------------|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Wartość ciągu, określając nazwę firmy.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Wartość, określając informacje o prawach autorskich ciągu.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Wartość ciągu, określając numeru wersji pliku systemu Win32. Domyślnie to zwykle wersji zestawu.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Wartość, określając informacje o wersji, który nie jest używany przez środowisko uruchomieniowe języka wspólnego, takie jak numer wersji pełnej produktu ciągu. **Uwaga:**  Jeśli ten atrybut jest stosowany do zestawu, określa ciąg znaków można uzyskać w czasie wykonywania za pomocą <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> właściwości. Ten ciąg jest również używany w ścieżce i kluczy rejestru dostarczone przez <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> właściwości.|  
|<xref:System.Reflection.AssemblyProductAttribute>|Wartość, określając informacje o produkcie ciągu.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Wartość, określając informacje o znakach towarowych ciągu.|  
  
 Te atrybuty może znajdować się na stronie właściwości Windows zestawu lub mogą być zastąpione, za pomocą **/win32res** opcję kompilatora, aby określić własny plik zasobów Win32.  
  
## <a name="assembly-manifest-attributes"></a>Atrybuty manifestu zestawu  
 Aby podać informacje w manifeście zestawu, w tym tytuł, opis, domyślny alias i konfiguracji, można użyć atrybutów manifestu zestawu. W poniższej tabeli opisano atrybuty manifestu zestawu.  
  
|Atrybut manifestu zestawu|Opis|  
|---------------------------------|-----------------|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Wartość wskazująca konfiguracji zestawu, na przykład sprzedaży detalicznej lub debugowania ciągu. Środowisko wykonawcze nie korzysta z tej wartości.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Wartość ciągu, określając domyślny alias, który będzie używany przez odwoływanie się do zestawów. Ta wartość określa przyjazną nazwę, gdy nazwa zestawu, sama nie jest przyjazna (na przykład wartość identyfikatora GUID). Ta wartość może służyć również jako krótka nazwa pełnego zestawu.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Wartość ciągu, określając krótki opis, który podsumowuje ujawnienia zestawu.|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Wartość ciągu, określając przyjazną nazwę dla zestawu. Na przykład zestaw o nazwie comdlg może zawierać tytuł Microsoft wspólne kontrolki okna dialogowego.|  
  
## <a name="strong-name-attributes"></a>Atrybuty silnej nazwy  
 Za pomocą silnej nazwy atrybutów można ustawić silną nazwę zestawu. W poniższej tabeli opisano atrybuty silnej nazwy.  
  
|Atrybuty silnej nazwy|Opis|  
|----------------------------|-----------------|  
|<xref:System.Reflection.AssemblyDelaySignAttribute>|Wartość logiczna wskazująca, czy opóźnienie podpisywania jest używany.|  
|<xref:System.Reflection.AssemblyKeyFileAttribute>|Wartość ciągu wskazujące nazwę pliku który zawiera albo klucza publicznego (jeśli jest używana, podpisywanie opóźnione) lub klucza publicznego i prywatnego przekazany jako parametr do konstruktora tego atrybutu. Należy pamiętać, że nazwa pliku jest względną ścieżką pliku wyjściowego (.exe lub .dll), nie ścieżka pliku źródłowego.|  
|<xref:System.Reflection.AssemblyKeyNameAttribute>|Określa kontener klucza, który zawiera pary kluczy przekazany jako parametr do konstruktora tego atrybutu.|  
  
 Poniższy przykład kodu pokazuje atrybuty do zastosowania, gdy za pomocą opóźnione podpisywanie do utworzenia zestawu z silną nazwą przy użyciu pliku klucza publicznego o nazwie `myKey.snk`.  
  
 [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
 [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
 [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)
- [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)
