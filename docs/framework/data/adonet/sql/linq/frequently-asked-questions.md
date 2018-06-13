---
title: Często zadawane pytania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 5f556c46823bd867709e8c53b59f7ac53201d242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365491"
---
# <a name="frequently-asked-questions"></a>Często zadawane pytania
Niektóre typowe problemy, które można napotkać podczas implementowania odpowiedzi na następujące sekcje [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 Dodatkowe problemy zostały rozwiązane w [Rozwiązywanie problemów](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
## <a name="cannot-connect"></a>Nie można połączyć z  
 Q. Nie można podłączyć do bazy danych.  
  
 A. Upewnij się, parametry połączenia są poprawne i czy działa wystąpienia programu SQL Server. Należy zauważyć, że [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wymaga włączenia protokołu potoków nazwanych. Aby uzyskać więcej informacji, zobacz [uczenia przez wskazówki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
## <a name="changes-to-database-lost"></a>Zmiany utracone w bazie danych  
 Q. Zmiany wprowadzone w danych w bazie danych, ale podczas I ponownie uruchomił aplikację, zmiany nie był już istnieje.  
  
 A. Upewnij się, że należy wywołać <xref:System.Data.Linq.DataContext.SubmitChanges%2A> być zapisane wyniki w bazie danych.  
  
## <a name="database-connection-open-how-long"></a>Połączenie z bazą danych: Otwórz czas?  
 Q. Jak długo połączenia z bazą danych pozostają otwarte?  
  
 A. Połączenie zazwyczaj pozostaje otwarty do momentu korzystać wyników zapytania. Jeśli chcesz wziąć czasu nie przetworzył wszystkich wyników i czy nie do wyników buforowania, zastosuj <xref:System.Linq.Enumerable.ToList%2A> do zapytania. W typowych scenariuszy, w których każdy obiekt jest przetwarzany tylko jeden raz, przesyłania strumieniowego model jest nadrzędny w obu `DataReader` i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Dokładne szczegóły dotyczące użycia połączenia są zależne od następujących czynności:  
  
-   Stan połączenia Jeśli <xref:System.Data.Linq.DataContext> jest tworzony za pomocą obiektu połączenia.  
  
-   Ustawień parametrów połączenia (na przykład dzięki wielu aktywnych zestawów wyników (MARS). Aby uzyskać więcej informacji, zobacz [wielu aktywnych zestawów wyników (MARS)](../../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md).  
  
## <a name="updating-without-querying"></a>Aktualizowanie bez wykonywania zapytania  
 Q. Bez pierwszej kwerendy bazy danych można zaktualizować tabeli danych?  
  
 A. Mimo że [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie ma aktualizacji na podstawie zestawu poleceń, można użyć jednej z następujących metod można zaktualizować bez pierwszej kwerendy:  
  
-   Użyj <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> wysłać kod SQL.  
  
-   Utwórz nowe wystąpienie obiektu i zainicjuj wszystkie bieżące wartości (pól) wpływających na tę aktualizację. Następnie dołączyć obiekt, aby <xref:System.Data.Linq.DataContext> przy użyciu <xref:System.Data.Linq.Table%601.Attach%2A> i zmodyfikuj pola, które chcesz zmienić.  
  
## <a name="unexpected-query-results"></a>Nieoczekiwane wyniki  
 Q. Zwraca nieoczekiwane wyniki kwerendy. Jak sprawdzić, co ma miejsce?  
  
 A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zawiera różne narzędzia umożliwiające zapoznanie się z kodu SQL, który generuje. Jednym z najważniejszych jest <xref:System.Data.Linq.DataContext.Log%2A>. Aby uzyskać więcej informacji, zobacz [obsługi debugowania](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).  
  
## <a name="unexpected-stored-procedure-results"></a>Procedura składowana nieoczekiwane wyniki  
 Q. Mam procedury składowanej, którego wartość zwracana jest obliczana na podstawie `MAX()`. Gdy przeciągnąć procedurę składowaną do [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] powierzchni, zwracana wartość jest nieprawidłowy.  
  
 A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zawiera zwracane wartości generowanych przez bazę danych i procedur składowanych na dwa sposoby:  
  
-   Za pomocą nazw wynik danych wyjściowych.  
  
-   Jawnie określając parametr wyjściowy.  
  
 Oto przykład nieprawidłowych danych wyjściowych. Ponieważ [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie może mapować wyniki, zawsze zwraca 0:  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select max(i) from t where name like 'hello'`  
  
 `end`  
  
 Poniżej przedstawiono przykład danych wyjściowych poprawne za pomocą parametru wyjściowego:  
  
 `create procedure proc2`  
  
 `@result int OUTPUT`  
  
 `as`  
  
 `select @result = MAX(i) from t where name like 'hello'`  
  
 `go`  
  
 Poniżej przedstawiono przykład danych wyjściowych poprawne za pomocą nazw wynik danych wyjściowych:  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select nax(i) AS MaxResult from t where name like 'hello'`  
  
 `end`  
  
 Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacji przez przy użyciu procedur składowanych](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md).  
  
## <a name="serialization-errors"></a>Błędy serializacji  
 Q. Podczas serializacji, pojawia się następujący błąd: "typu 'System.Data.Linq.ChangeTracker+StandardChangeTracker'... nie jest oznaczony jako możliwy do serializacji."  
  
 A. Generowanie w kodu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje <xref:System.Runtime.Serialization.DataContractSerializer> szeregowanie. Nie obsługuje <xref:System.Xml.Serialization.XmlSerializer> lub <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Aby uzyskać więcej informacji, zobacz [szeregowanie](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md).  
  
## <a name="multiple-dbml-files"></a>Wiele plików DBML  
 Q. Mam wiele plików DBML, które mają wspólną niektóre tabele pojawia się błąd kompilatora.  
  
 A. Ustaw **Namespace kontekstu** i **Namespace jednostki** właściwości z [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] różne wartości dla każdego pliku DBML. Takie podejście eliminuje kolizji nazw/przestrzeni nazw.  
  
## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a>Unikanie jawne ustawienie wartości generowanych przez bazę danych na Insert lub Update  
 Q. Mam tabeli bazy danych z `DateCreated` kolumny, która domyślnie SQL `Getdate()`. Podczas próby wstawienia nowego rekordu przy użyciu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], pobiera wartość `NULL`. Czy powinien mieć ustawioną wartość domyślną bazy danych.  
  
 A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje tej sytuacji automatycznie dla tożsamości (automatycznego przyrostu) i rowguidcol (identyfikator GUID generowany przez bazę danych) i kolumn znaczników czasu. W innych przypadkach należy ręcznie ustawić <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> = `true` i <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> = <xref:System.Data.Linq.Mapping.AutoSync.Always> / <xref:System.Data.Linq.Mapping.AutoSync.OnInsert> / <xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> właściwości.  
  
## <a name="multiple-dataloadoptions"></a>Wiele DataLoadOptions  
 Q. Opcje dodatkowe obciążenie można określić bez zastępowania pierwszy?  
  
 A. Tak. Pierwszy nie są zastępowane, jak w poniższym przykładzie:  
  
```vb  
Dim dlo As New DataLoadOptions()  
dlo.LoadWith(Of Order)(Function(o As Order) o.Customer)  
dlo.LoadWith(Of Order)(Function(o As Order) o.OrderDetails)  
```  
  
```csharp  
DataLoadOptions dlo = new DataLoadOptions();  
dlo.LoadWith<Order>(o => o.Customer);  
dlo.LoadWith<Order>(o => o.OrderDetails);  
```  
  
## <a name="errors-using-sql-compact-35"></a>Błędy przy użyciu programu SQL Compact 3,5  
 Q. Błąd podczas przeciągania tabel z [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)] bazy danych.  
  
 A. [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Nie obsługuje [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)], mimo że [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jest środowiska wykonawczego. W takiej sytuacji należy tworzenie własnych klas jednostki i dodaje odpowiednie atrybuty.  
  
## <a name="errors-in-inheritance-relationships"></a>Błędy w relacji dziedziczenia  
 Q. Po użyciu przybornika dziedziczenia kształtu [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nawiązać dwie jednostki, ale wystąpiły błędy.  
  
 A. Tworzenie relacji jest niewystarczająca. Należy podać informacje, takie jak kolumna dyskryminatora, wartość dyskryminatora klasy podstawowej i wartość dyskryminatora klasy pochodnej.  
  
## <a name="provider-model"></a>Dostawca modelu  
 Q. Model publiczny dostawca jest dostępny?  
  
 A. Żaden model publiczny dostawca jest dostępny. W tej chwili [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje program SQL Server i [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)] tylko.  
  
## <a name="sql-injection-attacks"></a>Ataki na wstrzyknięciu kodu SQL  
 Q. Jak jest [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] chronione przed atakami iniekcja kodu SQL?  
  
 A. Iniekcja kodu SQL została znaczące zagrożenie dla tradycyjnych zapytania SQL utworzone przez łączenie danych wejściowych użytkownika. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pozwala uniknąć takich iniekcji przy użyciu <xref:System.Data.SqlClient.SqlParameter> w zapytaniach. Dane wejściowe użytkownika jest włączona do wartości parametrów. Takie podejście uniemożliwia użycie z klienta w danych wejściowych polecenia złośliwe.  
  
## <a name="changing-read-only-flag-in-dbml-files"></a>Zmiana flagi tylko do odczytu w DBML, pliki  
 Q. Jak wyeliminować ustawiające z niektórych właściwości, podczas tworzenia modelu obiektów z pliku DBML?  
  
 A. Wykonaj następujące czynności w tym scenariuszu zaawansowane:  
  
1.  W pliku .dbml zmodyfikuj właściwość zmieniając <xref:System.Data.Linq.ITable.IsReadOnly%2A> flaga `True`.  
  
2.  Dodawanie klasy częściowej. Utwórz konstruktora z parametrami dla członków tylko do odczytu.  
  
3.  Przejrzyj domyślne <xref:System.Data.Linq.Mapping.UpdateCheck> wartość (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>), aby ustalić, czy jest poprawny dla aplikacji.  
  
    > [!CAUTION]
    >  Jeśli używasz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] w programie Visual Studio, zmiany mogą zostać zastąpione.  
  
## <a name="aptca"></a>APTCA  
 Q. Jest System.Data.Linq oznaczona do użytku przez kod częściowo zaufany?  
  
 A. Tak, to zestaw System.Data.Linq.dll między tymi [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] oznaczonej jako zestawy <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu. Bez tego oznaczania, zestawy w [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] są przeznaczone do użytku tylko w pełni zaufanego kodu.  
  
 Główna scenariusz w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dla stosowanie częściowo zaufane obiekty wywołujące jest umożliwienie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zestawu do będą uzyskiwać dostęp do aplikacji sieci Web, gdzie *zaufania* konfiguracji to średni.  
  
## <a name="mapping-data-from-multiple-tables"></a>Mapowanie danych z wielu tabel  
 Q. Dane w mojej jednostki pochodzą z wielu tabel. Sposób mapowania go  
  
 A. Można utworzyć widok w bazie danych i mapowania jednostki do widoku. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje tego samego SQL dla widoków, jak w przypadku tabel.  
  
> [!NOTE]
>  Korzystanie z widoków w tym scenariuszu ma pewne ograniczenia. Ta metoda działa najbezpieczniejszy gdy operacje są wykonywane na <xref:System.Data.Linq.Table%601> są obsługiwane przez źródłowego widoku. Tylko wiesz, jakie operacje są przeznaczone. Na przykład większość aplikacji są tylko do odczytu i wykonywania inny numer znaczne obciążenie `Create` / `Update` / `Delete` operacje tylko przy użyciu przechowywanych procedur przed widoków.  
  
## <a name="connection-pooling"></a>Pula połączeń  
 Q. Istnieje już konstrukcję, która może ułatwić <xref:System.Data.Linq.DataContext> buforowania?  
  
 A. Nie należy próbować ponowne użycie wystąpienia <xref:System.Data.Linq.DataContext>. Każdy <xref:System.Data.Linq.DataContext> zachowuje swój stan, (łącznie z pamięci podręcznej tożsamości) dla jednej sesji edycji/kwerendy. Aby uzyskać nowe wystąpienia, w oparciu o bieżący stan bazy danych, użyj nowego <xref:System.Data.Linq.DataContext>.  
  
 Można nadal używać bazowy [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] puli połączeń. Aby uzyskać więcej informacji, zobacz [programu SQL Server połączenia buforowanie (ADO.NET)](../../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
## <a name="second-datacontext-is-not-updated"></a>Drugi element DataContext nie jest aktualizowana.  
 Q. Użycie jednego wystąpienia <xref:System.Data.Linq.DataContext> wartości mają być przechowywane w bazie danych. Jednak drugiej <xref:System.Data.Linq.DataContext> na tej samej bazy danych nie odzwierciedla zaktualizowane wartości. Drugi <xref:System.Data.Linq.DataContext> wystąpienia wydaje się, aby zwrócić wartości pamięci podręcznej.  
  
 A. To zachowanie jest celowe. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] w dalszym ciągu zwrócić tego samego wystąpienia/wartości, które widać w pierwszej kolejności. Po dokonaniu aktualizacji, możesz użyć optymistycznej współbieżności. Oryginalnych danych służy do sprawdzania z bieżącym stanem bazy danych do potwierdzenia, że w rzeczywistości nadal jest bez zmian. Jeśli została ona zmieniona występuje konflikt, a aplikacji należy go rozwiązać. Jedną z opcji aplikacji jest, aby przywrócić oryginalny stan bieżący stan bazy danych i spróbuj ponownie przeprowadzić aktualizację. Aby uzyskać więcej informacji, zobacz [porady: Zarządzanie konfliktów zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
 Można również ustawić <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> na wartość false, która włącza wyłączone buforowanie i śledzenie zmian. Można następnie pobrać najnowsze wartości zawsze należy zbadać.  
  
## <a name="cannot-call-submitchanges-in-read-only-mode"></a>Nie można wywołać funkcji SubmitChanges w trybie tylko do odczytu  
 Q. Podczas próby wywołania <xref:System.Data.Linq.DataContext.SubmitChanges%2A> w trybie tylko do odczytu, jest zgłaszany błąd.  
  
 A. Tryb tylko do odczytu wyłącza możliwość kontekst śledzenia zmian.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [Rozwiązywanie problemów](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)  
 [Zabezpieczenia w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md)
