---
title: "Ustawienie atrybutów zestawu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f95d8c5f78dfa9ec388cfa63b81857ffe580abf3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="setting-assembly-attributes"></a>Ustawienie atrybutów zestawu
Atrybuty zestawu wartości, które zawierają informacje o zestawie. Atrybuty są podzielone na następujące zestawy informacji:  
  
-   Atrybuty tożsamości zestawu.  
  
-   Atrybuty informacyjny.  
  
-   Atrybutów manifestu zestawu.  
  
-   Atrybuty silnej nazwy.  
  
## <a name="assembly-identity-attributes"></a>Atrybuty tożsamości zestawu  
 Trzy atrybuty, wraz z nazwą silną (jeśli dotyczy) określić tożsamości zestawu: nazwa, wersja i kultury. Te atrybuty tworzą Pełna nazwa zestawu i są wymagane, gdy odwołanie do zestawu w kodzie. Atrybuty umożliwia ustawianie wersja zestawu i kultury. Kompilator lub [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) ustawia wartość nazwy, gdy zestaw jest tworzony na podstawie pliku zawierającego manifest zestawu.  
  
 W poniższej tabeli opisano atrybuty wersji i kultury.  
  
|Atrybut tożsamości zestawu|Opis|  
|---------------------------------|-----------------|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Pole wyliczany wskazujący kultura, która obsługuje zestaw. Zestaw można również określić niezależność od kultury, wskazujący, że zawiera on zasobów dla kultury domyślnej. **Uwaga:** środowiska uruchomieniowego traktuje zestawu, który nie ma atrybutu kultury ustawionej na wartość null jako zestaw satelicki. Takie zestawy obowiązują zasady powiązanie zestawu satelity. Aby uzyskać więcej informacji, zobacz [jak zestawy środowiska wykonawczego lokalizuje](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|Wartość, która ustawia zestawu atrybutów, takich jak czy zestawu można uruchamiać jednocześnie.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Wartość liczbowa w formacie *głównych*. *drobne*. *Tworzenie*. *poprawki* (na przykład 2.4.0.0). Środowisko uruchomieniowe języka wspólnego wykorzystuje tę wartość do wykonania operacji powiązanie w zestawy o silnych nazwach. **Uwaga:** Jeśli <xref:System.Reflection.AssemblyInformationalVersionAttribute> atrybut nie jest stosowany do zestawu, numer wersji określonej przez <xref:System.Reflection.AssemblyVersionAttribute> atrybut jest używany przez <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>, i <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> właściwości.|  
  
 Poniższy przykład kodu pokazuje, jak zastosować do zestawu atrybutów wersji i kultury.  
  
 [!code-cpp[AssemblyDelaySignAttribute#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#3)]
 [!code-csharp[AssemblyDelaySignAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#3)]
 [!code-vb[AssemblyDelaySignAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#3)]  
  
## <a name="informational-attributes"></a>Atrybuty informacyjny  
 Atrybuty informacyjną umożliwia zapewniają dodatkowe firmy lub informacji o produkcie dla zestawu. W poniższej tabeli opisano atrybuty informacyjne, które można zastosować do zestawu.  
  
|Atrybut informacyjny|Opis|  
|-----------------------------|-----------------|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|Ciąg określający nazwę firmy.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Określanie informacji o prawach autorskich wartość ciągu.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Ciąg określający numer wersji pliku Win32. Domyślnie to zwykle wersja zestawu.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Określanie informacji o wersji, który nie jest używany przez środowisko uruchomieniowe języka wspólnego, takich jak numer wersji pełnej produktu wartość ciągu. **Uwaga:** Jeśli ten atrybut jest stosowany do zestawu, ciąg Określa można uzyskać w czasie wykonywania za pomocą <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> właściwości. Ten ciąg jest również używany w ścieżce i rejestru klucza udostępnionego przez <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> właściwości.|  
|<xref:System.Reflection.AssemblyProductAttribute>|Określanie informacji o produkcie wartość ciągu.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Określanie informacje o znakach towarowych wartość ciągu.|  
  
 Te atrybuty mogą być wyświetlane na stronie właściwości systemu Windows zestawu lub może zostać zastąpiona, za pomocą **/win32res** opcję kompilatora, aby określić własny plik zasobów Win32.  
  
## <a name="assembly-manifest-attributes"></a>Atrybutów manifestu zestawu  
 Aby podać informacje w manifeście zestawu, w tym tytuł, opis, domyślny alias i konfiguracji, można użyć atrybutów manifestu zestawu. W poniższej tabeli opisano atrybuty manifestu zestawu.  
  
|Atrybut manifestu zestawu|Opis|  
|---------------------------------|-----------------|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Wartość wskazująca konfiguracji zestawu, na przykład detalicznych lub debugowanych ciągu. Środowisko uruchomieniowe nie korzysta z tej wartości.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Określanie alias domyślna ma być używany przez zestawy odwołujące wartość ciągu. Ta wartość określa przyjazną nazwę, gdy nazwa zestawu nie jest przyjazną (na przykład wartość identyfikatora GUID). Ta wartość może również jako Krótka forma pełną nazwą zestawu.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Wartość ciągu, określając krótki opis podsumowujący ujawnienia zestawu.|  
|<xref:System.Reflection.AssemblyTitleAttribute>|Wartość ciągu, określając przyjazną nazwę dla zestawu. Na przykład zestaw o nazwie comdlg może mieć tytuł formantu okna dialogowego wspólnego firmy Microsoft.|  
  
## <a name="strong-name-attributes"></a>Atrybuty silnej nazwy  
 Można użyć silnej nazwy atrybutów można ustawić silnej nazwy zestawu. W poniższej tabeli opisano atrybuty silnej nazwy.  
  
|Atrybuty silnej nazwy|Opis|  
|----------------------------|-----------------|  
|<xref:System.Reflection.AssemblyDelaySignAttribute>|Wartość logiczna wskazująca, że podpisywanie opóźnione jest używana.|  
|<xref:System.Reflection.AssemblyKeyFileAttribute>|Ciąg wskazujący nazwę pliku, który zawiera publicznego klucza (jeśli jest używana, podpisywanie opóźnione) lub kluczami publicznymi i prywatnymi przekazany jako parametr do konstruktora tego atrybutu. Należy pamiętać, że nazwa pliku względną ścieżką pliku wyjściowego (.exe lub .dll) nie jest ścieżki pliku źródłowego.|  
|<xref:System.Reflection.AssemblyKeyNameAttribute>|Określa kontener klucza, który zawiera pary kluczy przekazany jako parametr do konstruktora tego atrybutu.|  
  
 Poniższy przykład kodu pokazuje atrybuty do zastosowania po użyciu opóźnione podpisywanie można utworzyć zestawu z silną nazwą z pliku klucza publicznego o nazwie `myKey.snk`.  
  
 [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
 [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
 [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)  
 [Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)
