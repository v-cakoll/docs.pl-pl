---
title: Mapowanie opartych na atrybutach
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dd89999-f415-4d61-b8c8-237d23d7924e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a8397c106ec45d9e6e1e9ec513536142d3048bd7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="attribute-based-mapping"></a>Mapowanie opartych na atrybutach
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]mapuje bazy danych programu SQL Server do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modelu obiektu albo stosowanie atrybutów lub przy użyciu pliku mapowania zewnętrznych. W tym temacie przedstawiono podejście opartych na atrybutach.  
  
 W postaci najbardziej podstawowym [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mapy bazę danych do <xref:System.Data.Linq.DataContext>, tabeli, klasy i kolumn oraz relacji z właściwości dla tych klas. Umożliwia także atrybuty do mapowania hierarchii dziedziczenia w modelu obiektu. Aby uzyskać więcej informacji, zobacz [porady: Generowanie modelu obiektów w Visual Basic lub C#](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md).  
  
 Deweloperzy przy użyciu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] na ogół wykonać mapowania na podstawie atrybutów przy użyciu [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Można także użyć narzędzia wiersza polecenia SQLMetal, lub możesz ręcznie kod atrybuty samodzielnie. Aby uzyskać więcej informacji, zobacz [porady: Generowanie modelu obiektów w Visual Basic lub C#](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md).  
  
> [!NOTE]
>  Można również mapować przy użyciu zewnętrznego pliku XML. Aby uzyskać więcej informacji, zobacz [zewnętrznych mapowania](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
 W poniższych sekcjach opisano na podstawie atrybutów mapowania bardziej szczegółowo. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping> przestrzeni nazw.  
  
## <a name="databaseattribute-attribute"></a>Atrybut DatabaseAttribute  
 Ten atrybut umożliwia określenie domyślnej nazwy bazy danych, gdy nie podano nazwy dla tego połączenia. Ten atrybut jest opcjonalne, ale jeśli można go użyć, należy zastosować <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> właściwości, zgodnie z opisem w poniższej tabeli.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|String|Zobacz<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|Używane z jego <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> właściwość, określa nazwę bazy danych.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.DatabaseAttribute>.  
  
## <a name="tableattribute-attribute"></a>Atrybut TableAttribute  
 Ten atrybut umożliwia wyznacza klasę klasy jednostki, która jest skojarzona z tabeli bazy danych lub widoku. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]traktuje klasy, które mają atrybut jako trwałe klasy. W poniższej tabeli opisano <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> właściwości.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.TableAttribute.Name%2A>|String|Tych samych parametrach jako nazwa klasy|Określa klasę jako klasę jednostki skojarzonej z tabelą bazy danych.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
## <a name="columnattribute-attribute"></a>Atrybut klasy ColumnAttribute  
 Aby wyznaczyć członka klasy jednostki do reprezentowania kolumny w tabeli bazy danych, należy użyć tego atrybutu. Ten atrybut można stosować do dowolnego pola lub właściwości.  
  
 Tylko członkowie zidentyfikować jako kolumny są pobierane i utrwalone po [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapisuje zmiany w bazie danych. Elementy członkowskie bez tego atrybutu muszą być trwałe i nie są przesyłane do wstawienia lub aktualizacji.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>|Automatyczna synchronizacja|Nigdy nie|Powoduje, że środowisko uruchomieniowe języka wspólnego (CLR) do pobierania wartości po zakończeniu operacji insert lub update.<br /><br /> Opcje: Zawsze, nigdy OnUpdate, OnInsert.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>|Boolean|`true`|Wskazuje, że kolumna może zawierać wartości null.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>|String|Typ kolumny wnioskowany bazy danych|Typy bazy danych używa i modyfikatory, aby określić typ kolumny bazy danych.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>|String|Pusty|Definiuje kolumny obliczanej w bazie danych.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>|Boolean|`false`|Wskazuje, że kolumna zawiera wartości, które generuje automatycznie bazy danych.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A>|Boolean|`false`|Wskazuje, że kolumna zawiera wartości rozróżniacza [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] hierarchii dziedziczenia.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>|Boolean|`false`|Określa, że ten element członkowski klasy reprezentuje jest częścią kluczy podstawowych w tabeli lub kolumny.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>|Boolean|`false`|Określa typ kolumny elementu członkowskiego jako numer znacznika czasu lub wersji bazy danych.|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>|UpdateCheck|`Always`, chyba że <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> jest `true` dla elementu członkowskiego|Określa sposób [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zbliża się do wykrywania konfliktów optymistycznej współbieżności.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
> [!NOTE]
>  Wartości właściwości AssociationAttribute i klasy ColumnAttribute magazynu jest uwzględniana wielkość liter. Na przykład upewnij się, czy wartości używanych w atrybucie dla właściwości AssociationAttribute.Storage zgodne w przypadku odpowiadających im nazw właściwości używane w innym miejscu w kodzie. Dotyczy to wszystkich .NET języków programowania, nawet te, które nie są zwykle z uwzględnieniem wielkości liter, w tym [!INCLUDE[vb_current_short](../../../../../../includes/vb-current-short-md.md)]. Aby uzyskać więcej informacji na temat właściwości magazynu, zobacz <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
## <a name="associationattribute-attribute"></a>Atrybut AssociationAttribute  
 Można określić właściwości do reprezentowania skojarzenia w bazie danych, takich jak klucza obcego do relacji klucza podstawowego, należy użyć tego atrybutu. Aby uzyskać więcej informacji na temat relacji, zobacz [porady: relacje bazy danych mapy](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md).  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteOnNull%2A>|Boolean|`false`|Po umieszczeniu na skojarzenie, której członkowie klucza obcego są wszystkie dopuszcza wartości null, usuwa obiekt, gdy skojarzenie jest ustawiona na wartość null.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteRule%2A>|String|Brak|Dodaje zachowanie usuwania skojarzenia.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsForeignKey%2A>|Boolean|`false`|Jeśli PRAWDA, określa element członkowski jako klucz obcy w skojarzeniu reprezentujący relacje bazy danych.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsUnique%2A>|Boolean|`false`|Jeśli ma wartość true, wskazuje ograniczenie unikatowości klucza obcego.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A>|String|Identyfikator klasy pokrewne|Określa co najmniej jednego członka klasy docelowej jednostki jako wartości kluczy po drugiej stronie skojarzenia.|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.ThisKey%2A>|String|Identyfikator klasy zawierające|Określa elementy członkowskie tej klasy jednostki do reprezentowania wartości klucza na tej stronie skojarzenia.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.AssociationAttribute>.  
  
> [!NOTE]
>  Wartości właściwości AssociationAttribute i klasy ColumnAttribute magazynu jest uwzględniana wielkość liter. Na przykład upewnij się, czy wartości używanych w atrybucie dla właściwości AssociationAttribute.Storage zgodne w przypadku odpowiadających im nazw właściwości używane w innym miejscu w kodzie. Dotyczy to wszystkich .NET języków programowania, nawet te, które nie są zwykle z uwzględnieniem wielkości liter, w tym [!INCLUDE[vb_current_short](../../../../../../includes/vb-current-short-md.md)]. Aby uzyskać więcej informacji na temat właściwości magazynu, zobacz <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.  
  
## <a name="inheritancemappingattribute-attribute"></a>Atrybut InheritanceMappingAttribute  
 Ten atrybut umożliwia mapowania hierarchii dziedziczenia.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>|String|Brak. Należy podać wartość.|Określa wartość kodu rozróżniacza.|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>|Boolean|`false`|Jeśli PRAWDA, tworzy wystąpienie tego typu obiektu, gdy żadna wartość dyskryminatora w magazynie dopasowuje dowolny z określonymi wartościami.|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>|Typ|Brak. Należy podać wartość.|Określa typ klasy w hierarchii.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>.  
  
## <a name="functionattribute-attribute"></a>Atrybut FunctionAttribute  
 Aby określić metodę reprezentujący procedura składowana lub funkcja zdefiniowana przez użytkownika w bazie danych, należy użyć tego atrybutu.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A>|Boolean|`false`|W przypadku wartości FAŁSZ wskazuje mapowanie do procedury składowanej. Jeśli ma wartość true, wskazuje mapowanie do funkcji zdefiniowanej przez użytkownika.|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.Name%2A>|String|Tych samych parametrach jako nazwy w bazie danych|Określa nazwę procedury składowanej lub funkcji zdefiniowanej przez użytkownika.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.FunctionAttribute>.  
  
## <a name="parameterattribute-attribute"></a>Atrybut ParameterAttribute  
 Ten atrybut umożliwia mapowanie parametrów wejściowych dla procedury składowanej metod.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.DbType%2A>|String|Brak|Określa typ bazy danych.|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.Name%2A>|String|Tych samych parametrach jako nazwę parametru w bazie danych|Określa nazwę parametru.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ParameterAttribute>.  
  
## <a name="resulttypeattribute-attribute"></a>Atrybut ResultTypeAttribute  
 Ten atrybut umożliwia określenie typu wyniku.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ResultTypeAttribute.Type%2A>|Typ|(Brak)|Używane w metodach mapowane na procedury składowane, które zwracają <xref:System.Data.Linq.IMultipleResults>. Deklaruje mapowania prawidłowe lub oczekiwanego typu dla procedury składowanej.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ResultTypeAttribute>.  
  
## <a name="dataattribute-attribute"></a>Atrybut DataAttribute  
 Ten atrybut umożliwia określenie nazwy i pola prywatne magazynu.  
  
 W poniższej tabeli opisano właściwości tego atrybutu.  
  
|Właściwość|Typ|Domyślny|Opis|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Name%2A>|String|Taka sama jak nazwa bazy danych|Określa nazwę tabeli, kolumny i tak dalej.|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>|String|Metody dostępu publicznego|Określa nazwę pola podstawowego magazynu.|  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.DataAttribute>.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
