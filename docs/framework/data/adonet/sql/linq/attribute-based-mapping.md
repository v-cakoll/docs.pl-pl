---
title: Mapowanie oparte na atrybutach
ms.date: 03/30/2017
ms.assetid: 6dd89999-f415-4d61-b8c8-237d23d7924e
ms.openlocfilehash: 41152aa81ab84a2ab77e9a4ebf16e102ee5c0e3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964093"
---
# <a name="attribute-based-mapping"></a>Mapowanie oparte na atrybutach
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]mapuje bazę danych SQL Server na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] model obiektu przez zastosowanie atrybutów lub zewnętrznego pliku mapowania. Ten temat zawiera opis podejścia opartego na atrybutach.  
  
 W najpopularniejszym formularzu podstawowym program [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapuje bazę danych <xref:System.Data.Linq.DataContext>do tabeli, tabelę na klasę, a następnie kolumny i relacje z właściwościami tych klas. Można również użyć atrybutów do mapowania hierarchii dziedziczenia w modelu obiektów. Aby uzyskać więcej informacji, zobacz [jak: Generuj model obiektów w Visual Basic lub C# ](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md).  
  
 Deweloperzy korzystający z programu Visual Studio zwykle wykonują mapowanie oparte na atrybutach przy użyciu Object Relational Designer. Możesz również użyć narzędzia wiersza polecenia SQLMetal lub samodzielnie pokodować atrybuty. Aby uzyskać więcej informacji, zobacz [jak: Generuj model obiektów w Visual Basic lub C# ](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md).  
  
> [!NOTE]
> Możesz również mapować przy użyciu zewnętrznego pliku XML. Aby uzyskać więcej informacji, zobacz [Mapowanie zewnętrzne](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
 W poniższych sekcjach opisano mapowanie oparte na atrybutach bardziej szczegółowo. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping> przestrzeń nazw.  
  
## <a name="databaseattribute-attribute"></a>DatabaseAttribute — atrybut  
 Użyj tego atrybutu, aby określić domyślną nazwę bazy danych, gdy nazwa nie jest dostarczana przez połączenie. Ten atrybut jest opcjonalny, ale jeśli jest używany, należy zastosować <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> właściwość, zgodnie z opisem w poniższej tabeli.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|String|Wyświetlania<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|Używany z <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> właściwością, określa nazwę bazy danych.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.DatabaseAttribute>.  
  
## <a name="tableattribute-attribute"></a>TableAttribute — atrybut  
 Ten atrybut służy do wyznaczania klasy jako klasy jednostki skojarzonej z tabelą lub widokiem bazy danych. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]traktuje klasy, które mają ten atrybut jako klas trwałych. W poniższej tabeli opisano <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> właściwość.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.TableAttribute.Name%2A>|String|Ten sam ciąg jako nazwę klasy|Wyznacza klasę jako klasę jednostki skojarzoną z tabelą bazy danych.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
## <a name="columnattribute-attribute"></a>ColumnAttribute — atrybut  
 Użyj tego atrybutu, aby wyznaczyć element członkowski klasy Entity do reprezentowania kolumny w tabeli bazy danych. Ten atrybut można zastosować do dowolnego pola lub właściwości.  
  
 Tylko elementy członkowskie identyfikowane jako kolumny są pobierane i utrwalane [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podczas zapisywania zmian w bazie danych. Nie przyjmuje się elementów członkowskich bez tego atrybutu jako nietrwałych i nie są one przesłane do operacji INSERT ani Update.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>|AutoSync|nigdy nie|Powoduje, że środowisko uruchomieniowe języka wspólnego (CLR) Pobiera wartość po operacji INSERT lub Update.<br /><br /> Opcje: Zawsze, nigdy, OnUpdate, OnInsert.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>|Boolean|`true`|Wskazuje, że kolumna może zawierać wartości null.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>|String|Typ kolumny wywnioskowanej bazy danych|Używa typów i modyfikatorów baz danych, aby określić typ kolumny bazy danych.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>|String|Pusty|Definiuje kolumnę obliczaną w bazie danych.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>|Boolean|`false`|Wskazuje, że kolumna zawiera wartości generowane automatycznie przez bazę danych.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A>|Boolean|`false`|Wskazuje, że kolumna zawiera wartość rozróżniacza dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] hierarchii dziedziczenia.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>|Boolean|`false`|Określa, że ten element członkowski klasy reprezentuje kolumnę, która jest lub jest częścią kluczy podstawowych tabeli.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>|Boolean|`false`|Identyfikuje typ kolumny elementu członkowskiego jako sygnaturę czasową bazy danych lub numer wersji.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>|UpdateCheck|`Always`, chyba <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> że `true` jest dla elementu członkowskiego|Określa sposób [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wykrywania optymistycznych konfliktów współbieżności.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
> [!NOTE]
> W wartościach właściwości magazynu AssociationAttribute i ColumnAttribute jest uwzględniana wielkość liter. Na przykład upewnij się, że wartości używane w atrybucie właściwości AssociationAttribute. Storage pasują do wielkości liter dla odpowiednich nazw właściwości używanych w innym miejscu w kodzie. Dotyczy to wszystkich języków programowania .NET, nawet tych, które nie są zazwyczaj rozróżniane wielkości liter, w tym Visual Basic. Aby uzyskać więcej informacji na temat właściwości Storage, <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>Zobacz.  
  
## <a name="associationattribute-attribute"></a>AssociationAttribute — atrybut  
 Użyj tego atrybutu, aby wyznaczyć Właściwość reprezentującą skojarzenie w bazie danych, takie jak klucz obcy do relacji klucza podstawowego. Aby uzyskać więcej informacji na temat relacji [, zobacz How to: Mapowanie relacji między](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md)bazami danych.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteOnNull%2A>|Boolean|`false`|Po umieszczeniu na skojarzeniu, którego składowe kluczy obcych są wszystkie niedopuszczające wartości null, usuwa obiekt, gdy skojarzenie ma wartość null.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteRule%2A>|String|Brak|Dodaje zachowanie usuwania do skojarzenia.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsForeignKey%2A>|Boolean|`false`|W przypadku wartości true wyznacza element członkowski jako klucz obcy w skojarzeniu reprezentującym relację bazy danych.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsUnique%2A>|Boolean|`false`|W przypadku wartości true wskazuje unikatowość ograniczenia klucza obcego.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A>|String|Identyfikator powiązanej klasy|Określa co najmniej jeden element członkowski klasy jednostki docelowej jako wartości klucza po drugiej stronie skojarzenia.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.ThisKey%2A>|String|Identyfikator klasy zawierającej|Wyznacza elementy członkowskie tej klasy jednostki, aby reprezentować wartości klucza po tej stronie skojarzenia.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.AssociationAttribute>.  
  
> [!NOTE]
> W wartościach właściwości magazynu AssociationAttribute i ColumnAttribute jest uwzględniana wielkość liter. Na przykład upewnij się, że wartości używane w atrybucie właściwości AssociationAttribute. Storage pasują do wielkości liter dla odpowiednich nazw właściwości używanych w innym miejscu w kodzie. Dotyczy to wszystkich języków programowania .NET, nawet tych, które nie są zazwyczaj rozróżniane wielkości liter, w tym Visual Basic. Aby uzyskać więcej informacji na temat właściwości Storage, <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>Zobacz.  
  
## <a name="inheritancemappingattribute-attribute"></a>InheritanceMappingAttribute — atrybut  
 Użyj tego atrybutu, aby zmapować hierarchię dziedziczenia.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>|String|Brak. Należy podać wartość.|Określa wartość kodu rozróżniacza.|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>|Boolean|`false`|Jeśli wartość jest równa true, tworzy wystąpienie obiektu tego typu, gdy żadna wartość rozróżniacza w sklepie nie pasuje do żadnej z określonych wartości.|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>|Typ|Brak. Należy podać wartość.|Określa typ klasy w hierarchii.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>.  
  
## <a name="functionattribute-attribute"></a>FunctionAttribute — atrybut  
 Użyj tego atrybutu, aby wyznaczyć metodę w postaci procedury składowanej lub funkcji zdefiniowanej przez użytkownika w bazie danych.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A>|Boolean|`false`|W przypadku wartości false oznacza mapowanie do procedury składowanej. W przypadku wartości true oznacza mapowanie do funkcji zdefiniowanej przez użytkownika.|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.Name%2A>|String|Ten sam ciąg jako nazwę w bazie danych|Określa nazwę procedury składowanej lub funkcji zdefiniowanej przez użytkownika.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.FunctionAttribute>.  
  
## <a name="parameterattribute-attribute"></a>ParameterAttribute — atrybut  
 Ten atrybut służy do mapowania parametrów wejściowych w metodach procedury składowanej.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.DbType%2A>|String|Brak|Określa typ bazy danych.|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.Name%2A>|String|Ten sam ciąg jako nazwę parametru w bazie danych|Określa nazwę parametru.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ParameterAttribute>.  
  
## <a name="resulttypeattribute-attribute"></a>Resultattribute — atrybut  
 Użyj tego atrybutu, aby określić typ wyniku.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ResultTypeAttribute.Type%2A>|Typ|Dawaj|Używane dla metod zamapowanych na procedury składowane, które zwracają <xref:System.Data.Linq.IMultipleResults>. Deklaruje prawidłowe lub oczekiwane mapowania typów dla procedury składowanej.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ResultTypeAttribute>.  
  
## <a name="dataattribute-attribute"></a>DataAttribute — atrybut  
 Użyj tego atrybutu, aby określić nazwy i pola prywatnego magazynu.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Name%2A>|String|Taka sama jak nazwa w bazie danych|Określa nazwę tabeli, kolumny i tak dalej.|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>|String|Publiczne metody dostępu|Określa nazwę bazowego pola magazynu.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.DataAttribute>.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
