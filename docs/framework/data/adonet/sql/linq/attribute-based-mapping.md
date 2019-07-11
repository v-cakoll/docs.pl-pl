---
title: Mapowanie oparte na atrybutach
ms.date: 03/30/2017
ms.assetid: 6dd89999-f415-4d61-b8c8-237d23d7924e
ms.openlocfilehash: a524e37640959c20c9883aa68e978a89428e43a4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743616"
---
# <a name="attribute-based-mapping"></a>Mapowanie oparte na atrybutach
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapuje bazę danych programu SQL Server do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modelu obiektowego przez albo stosowanie atrybutów lub przy użyciu pliku mapowanie zewnętrzne. W tym temacie opisano podejście oparte na atrybutach.  
  
 W postaci najbardziej podstawowe [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapuje bazę danych do <xref:System.Data.Linq.DataContext>, tabeli klasy, kolumny i relacje z właściwościami w tych klas. Atrybuty umożliwia również mapowanie hierarchii dziedziczenia w modelu obiektu. Aby uzyskać więcej informacji, zobacz [jak: Generowanie modelu obiektu w języku Visual Basic lub C# ](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md).  
  
 Deweloperzy korzystający z programu Visual Studio zwykle wykonać mapowanie oparte na atrybutach za pomocą Object Relational Designer. Można również użyć narzędzia wiersza polecenia SQLMetal albo można kodować ręcznie atrybuty samodzielnie. Aby uzyskać więcej informacji, zobacz [jak: Generowanie modelu obiektu w języku Visual Basic lub C# ](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md).  
  
> [!NOTE]
>  Można również mapować przy użyciu zewnętrznego pliku XML. Aby uzyskać więcej informacji, zobacz [mapowanie zewnętrzne](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
 W poniższych sekcjach opisano opartych na atrybutach mapowania bardziej szczegółowo. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping> przestrzeni nazw.  
  
## <a name="databaseattribute-attribute"></a>Atrybut DatabaseAttribute  
 Ten atrybut umożliwia określenie domyślnej nazwy bazy danych, gdy nazwy nie są dostarczane przez połączenie. Ten atrybut jest opcjonalny, ale jeśli jest ona używana, należy najpierw zastosować <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> właściwości, zgodnie z opisem w poniższej tabeli.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|String|Zobacz <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|Używane z jego <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> właściwość określa nazwę bazy danych.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.DatabaseAttribute>.  
  
## <a name="tableattribute-attribute"></a>Atrybut TableAttribute  
 Użyj tego atrybutu, aby wyznaczyć klasę jako klasa jednostki, który jest skojarzony z tabeli bazy danych lub widoku. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traktuje klas, które mają atrybut jako trwałe klasy. W poniższej tabeli opisano <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> właściwości.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.TableAttribute.Name%2A>|String|Ten sam ciąg jako nazwę klasy|Określa klasę jako klasę jednostki skojarzonej z tabelą bazy danych.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
## <a name="columnattribute-attribute"></a>Atrybut ColumnAttribute  
 Użyj tego atrybutu aby wyznaczyć składową klasy jednostki do reprezentowania kolumny w tabeli bazy danych. Ten atrybut można zastosować do żadnego pola ani właściwości.  
  
 Tylko członkowie zidentyfikować jako kolumny są pobierane i zachowywane po [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapisuje zmiany w bazie danych. Elementy członkowskie bez tego atrybutu to zakłada się, że trwałe i nie zostało przesłane do wstawienia lub aktualizacji.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>|AutoSync|nigdy nie|Powoduje, że środowisko uruchomieniowe języka wspólnego (CLR), aby pobrać wartość po operacji wstawiania lub aktualizacji.<br /><br /> Opcje: Zawsze nigdy, OnUpdate, wartość OnInsert.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>|Boolean|`true`|Wskazuje, że kolumna może zawierać wartości null.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>|String|Typ kolumny wywnioskowane bazy danych|Korzysta z typów bazy danych i modyfikatory, określ typ kolumny bazy danych.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>|String|Pusty|Definiuje kolumny obliczanej w bazie danych.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>|Boolean|`false`|Wskazuje, że kolumna zawiera wartości, które generuje automatycznie bazy danych.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A>|Boolean|`false`|Wskazuje, że kolumna zawiera wartość dyskryminatora [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] hierarchii dziedziczenia.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>|Boolean|`false`|Określa, czy ten element członkowski klasy odpowiada kolumnie lub jest częścią kluczy podstawowych w tabeli.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>|Boolean|`false`|Identyfikuje typ kolumny elementu członkowskiego jako numer znacznika czasu lub wersja bazy danych.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>|UpdateCheck|`Always`, chyba że <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> jest `true` dla członka|Określa, jak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zbliża się do wykrywania konfliktów optymistycznej współbieżności.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
> [!NOTE]
>  Wartości właściwości AssociationAttribute i ColumnAttribute magazynu uwzględniają wielkość liter. Na przykład upewnij się, że wartości używanych w atrybucie właściwości AssociationAttribute.Storage odpowiadać wielkości liter dla odpowiedniej nazwy właściwości używane w innych miejscach w kodzie. Dotyczy to wszystkich języków programowania .NET, nawet te, które nie są zwykle z uwzględnieniem wielkości liter, w tym Visual Basic. Aby uzyskać więcej informacji na temat właściwości magazynu zobacz <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
## <a name="associationattribute-attribute"></a>Atrybut AssociationAttribute  
 Użyj tego atrybutu, aby wyznaczyć właściwość, która ma reprezentować asocjacje w bazie danych, takie jak klucz obcy, aby relacji klucza podstawowego. Aby uzyskać więcej informacji na temat relacji, zobacz [jak: Mapowanie relacji w bazie danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md).  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteOnNull%2A>|Boolean|`false`|Po umieszczeniu na skojarzenie, w której obcych kluczy należą wszystkie wartości null, usuwa obiekt, gdy skojarzenie jest ustawiona na wartość null.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteRule%2A>|String|Brak|Dodaje zachowanie dotyczące usuwania skojarzenia.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsForeignKey%2A>|Boolean|`false`|W przypadku opcji true określa element członkowski, jako klucza obcego w asocjacji reprezentująca relacje bazy danych.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsUnique%2A>|Boolean|`false`|W przypadku opcji true oznacza ograniczenie unikatowości klucza obcego.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A>|String|Identyfikator klasy pokrewne|Określa co najmniej jednego członka klasy docelowej jednostki jako wartości klucza po drugiej stronie skojarzenia.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.ThisKey%2A>|String|Identyfikator klasy zawierającej|Określa elementy członkowskie tej klasy jednostki do reprezentowania wartości klucza tej stronie skojarzenia.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.AssociationAttribute>.  
  
> [!NOTE]
>  Wartości właściwości AssociationAttribute i ColumnAttribute magazynu uwzględniają wielkość liter. Na przykład upewnij się, że wartości używanych w atrybucie właściwości AssociationAttribute.Storage odpowiadać wielkości liter dla odpowiedniej nazwy właściwości używane w innych miejscach w kodzie. Dotyczy to wszystkich języków programowania .NET, nawet te, które nie są zwykle z uwzględnieniem wielkości liter, w tym Visual Basic. Aby uzyskać więcej informacji na temat właściwości magazynu zobacz <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
## <a name="inheritancemappingattribute-attribute"></a>Atrybut InheritanceMappingAttribute  
 Ten atrybut umożliwia mapowanie hierarchii dziedziczenia.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>|String|Brak. Wartość musi być podana.|Określa wartość kodu rozróżniacza.|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>|Boolean|`false`|W przypadku wartości true tworzy wystąpienie obiektu tego typu, gdy żadna wartość dyskryminatora magazynu jest zgodna z jednym z określonymi wartościami.|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>|Typ|Brak. Wartość musi być podana.|Określa typ klasy, w hierarchii.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>.  
  
## <a name="functionattribute-attribute"></a>Atrybut FunctionAttribute  
 Użyj tego atrybutu, aby wyznaczyć metody reprezentująca procedurę składowaną lub funkcję zdefiniowaną przez użytkownika w bazie danych.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A>|Boolean|`false`|W przypadku wartości FAŁSZ wskazuje mapowanie do procedury składowanej. W przypadku opcji true wskazuje mapowanie funkcji zdefiniowanej przez użytkownika.|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.Name%2A>|String|Ten sam ciąg jako nazwę w bazie danych|Określa nazwę procedury składowanej lub funkcji zdefiniowanej przez użytkownika.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.FunctionAttribute>.  
  
## <a name="parameterattribute-attribute"></a>Atrybut ParameterAttribute  
 Użyj tego atrybutu, aby zamapować parametry wejściowe dla procedury składowanej metod.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.DbType%2A>|String|Brak|Określa typ bazy danych.|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.Name%2A>|String|Ten sam ciąg jako nazwę parametru w bazie danych|Określa nazwę parametru.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ParameterAttribute>.  
  
## <a name="resulttypeattribute-attribute"></a>Atrybut ResultTypeAttribute  
 Użyj tego atrybutu, aby określić typ wyniku.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ResultTypeAttribute.Type%2A>|Typ|(Brak)|Używane w metodach mapowany do procedur składowanych, które zwracają <xref:System.Data.Linq.IMultipleResults>. Deklaruje mapowania prawidłowe lub oczekiwanego typu dla procedury składowanej.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ResultTypeAttribute>.  
  
## <a name="dataattribute-attribute"></a>Atrybut DataAttribute  
 Aby określić nazwy i pól magazynu prywatnego, należy użyć tego atrybutu.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Name%2A>|String|Taka sama jak nazwa bazy danych|Określa nazwę tabeli, kolumny i tak dalej.|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>|String|Publiczne metody dostępu|Określa nazwę pola podstawowego magazynu.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.DataAttribute>.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
