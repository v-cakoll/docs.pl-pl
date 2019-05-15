---
title: Często zadawane pytania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 4a41eac3d5b51936ebbae8d9e3dcf623da676bce
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583480"
---
# <a name="frequently-asked-questions"></a>Często zadawane pytania
Poniższe sekcje odpowiedzi na niektóre typowe problemy, które można napotkać podczas implementowania [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 Dodatkowe problemy zostały rozwiązane w [Rozwiązywanie problemów](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
## <a name="cannot-connect"></a>Nie można nawiązać połączenia  
 PYTANIE: Nie można nawiązać połączenia bazy danych.  
  
 A. Upewnij się, że parametry połączenia są poprawne, a wystąpienia programu SQL Server jest uruchomiona. Należy zauważyć, że [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wymaga włączenia protokołu potoków nazwanych. Aby uzyskać więcej informacji, zobacz [nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
## <a name="changes-to-database-lost"></a>Zmiany do bazy danych, utracone  
 PYTANIE: Zmiana dokonana w bazie danych, ale gdy I ponownie uruchomił aplikację, zmiany nie był już istnieje.  
  
 A. Upewnij się, że wywołanie <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Aby zapisać wyniki w bazie danych.  
  
## <a name="database-connection-open-how-long"></a>Połączenie z bazą danych: Jak długo otworzyć?  
 PYTANIE: Jak długo połączenia z bazą danych pozostają otwarte?  
  
 A. Połączenie zazwyczaj pozostaje otwarty do momentu używać wyników zapytania. Jeśli spodziewasz się trwać do przetwarzania wyników i czy nie w przeciwieństwie do buforowania wyniki, zastosuj <xref:System.Linq.Enumerable.ToList%2A> do zapytania. W typowych scenariuszach, w których każdy obiekt jest przetwarzany tylko raz, model przesyłania strumieniowego jest najlepsza w obu `DataReader` i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Szczegółowymi informacjami na temat użycia połączenia są zależne od następujących czynników:  
  
- Stan połączenia Jeśli <xref:System.Data.Linq.DataContext> jest zbudowany z obiektu połączenia.  
  
- Ustawienia parametrów połączenia (na przykład, dzięki czemu wielu aktywnych zestawów wyników (MARS). Aby uzyskać więcej informacji, zobacz [wielu aktywnych zestawów wyników (MARS)](../../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md).  
  
## <a name="updating-without-querying"></a>Aktualizowanie bez wykonywania zapytań  
 PYTANIE: Czy mogę zaktualizować dane w tabeli bez zapytanie do bazy danych?  
  
 A. Mimo że [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie ma aktualizacji na podstawie zestawu poleceń, używasz jednej z następujących metod można zaktualizować bez pierwszego zapytania:  
  
- Użyj <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> wysłać kod SQL.  
  
- Utwórz nowe wystąpienie obiektu i zainicjuj wszystkie bieżące wartości (pola), które mają wpływ na aktualizację. Następnie Dołącz obiekt do <xref:System.Data.Linq.DataContext> przy użyciu <xref:System.Data.Linq.Table%601.Attach%2A> i modyfikować zawartości pola, które chcesz zmienić.  
  
## <a name="unexpected-query-results"></a>Nieoczekiwane wyniki  
 PYTANIE: Moje zapytanie zwraca nieoczekiwane wyniki. Jak sprawdzić, co się dzieje?  
  
 A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zawiera różne narzędzia umożliwiające zapoznanie się z kodu SQL, który generuje. Jednym z najważniejszych jest <xref:System.Data.Linq.DataContext.Log%2A>. Aby uzyskać więcej informacji, zobacz [obsługę debugowania](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).  
  
## <a name="unexpected-stored-procedure-results"></a>Procedury składowanej nieoczekiwane wyniki  
 PYTANIE: Mam procedury składowanej, którego wartość zwracana jest obliczana na podstawie `MAX()`. Podczas przeciągania procedurę przechowywaną, aby [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] powierzchni, wartość zwracana nie jest prawidłowy.  
  
 A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Umożliwia zwracanie wartości wygenerowanych w bazie danych za pomocą procedur składowanych na dwa sposoby:  
  
- Za pomocą nazw danych wyjściowych.  
  
- Jawnie określając parametr wyjściowy.  
  
 Oto przykład nieprawidłowych danych wyjściowych. Ponieważ [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie można zamapować te wyniki zawsze zwraca 0:  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select max(i) from t where name like 'hello'`  
  
 `end`  
  
 Oto przykład poprawne dane wyjściowe przy użyciu parametru wyjściowego:  
  
 `create procedure proc2`  
  
 `@result int OUTPUT`  
  
 `as`  
  
 `select @result = MAX(i) from t where name like 'hello'`  
  
 `go`  
  
 Oto przykład poprawne dane wyjściowe za pomocą nazw danych wyjściowych:  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select nax(i) AS MaxResult from t where name like 'hello'`  
  
 `end`  
  
 Aby uzyskać więcej informacji, zobacz [Dostosowywanie operacje, przy użyciu procedur składowanych](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md).  
  
## <a name="serialization-errors"></a>Błędy serializacji  
 PYTANIE: Podczas próby serializacji, pojawia się następujący błąd: "Wpisz 'System.Data.Linq.ChangeTracker+StandardChangeTracker'... nie jest oznaczony jako możliwy do serializacji."  
  
 A. Generowanie w kodu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje <xref:System.Runtime.Serialization.DataContractSerializer> serializacji. Nie obsługuje <xref:System.Xml.Serialization.XmlSerializer> lub <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Aby uzyskać więcej informacji, zobacz [serializacji](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md).  
  
## <a name="multiple-dbml-files"></a>Wiele DBML, pliki  
 PYTANIE: Mam wiele DBML, pliki, które współużytkują wspólną niektórych tabel, pojawia się błąd kompilatora.  
  
 A. Ustaw **Namespace kontekstu** i **Namespace jednostki** właściwości z [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] różne wartości dla każdego pliku DBML. To podejście pozwala wyeliminować kolizji nazw/obszaru nazw.  
  
## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a>Unikanie jawne ustawienie wartości generowanych przez bazę danych na Insert nebo Update  
 PYTANIE: Czy mogę mieć tabelę zawierającą bazy danych `DateCreated` kolumny, która domyślnie SQL `Getdate()`. Podczas próby wstawienia nowego rekordu przy użyciu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], pobiera wartość `NULL`. Czy powinien mieć wartość domyślne bazy danych.  
  
 A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje taką sytuację automatycznie dla tożsamości (automatycznego przyrostu) i rowguidcol (identyfikator GUID generowany przez bazy danych) i kolumn sygnatur czasowych. W innych przypadkach należy ręcznie ustawić <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> = `true` i <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> = <xref:System.Data.Linq.Mapping.AutoSync.Always> / <xref:System.Data.Linq.Mapping.AutoSync.OnInsert> / <xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> właściwości.  
  
## <a name="multiple-dataloadoptions"></a>Multiple DataLoadOptions  
 PYTANIE: Czy można określić opcje dodatkowe obciążenie, bez zastępowania pierwszy?  
  
 A. Tak. Pierwszy nie jest zastępowany, jak w poniższym przykładzie:  
  
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
  
## <a name="errors-using-sql-compact-35"></a>Błędy przy użyciu języka SQL Compact 3.5  
 PYTANIE: Otrzymuję komunikat o błędzie podczas przeciągania tabel z [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)] bazy danych.  
  
 A. [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Nie obsługuje [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)], mimo że [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jest środowiska wykonawczego. W takiej sytuacji należy tworzenia własnych klas jednostek i dodawanie odpowiednich atrybutów.  
  
## <a name="errors-in-inheritance-relationships"></a>Błędy w relacjach dziedziczenia  
 PYTANIE: Po użyciu kształtu dziedziczenia przybornika w [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nawiązać dwie jednostki, ale występują błędy.  
  
 A. Tworzenie relacji jest niewystarczająca. Musisz podać informacje takie jak kolumna dyskryminatora, wartość dyskryminatora klasy bazowej i wartość dyskryminatora klasy pochodnej.  
  
## <a name="provider-model"></a>Dostawca modelu  
 PYTANIE: Model publiczny dostawca jest dostępny?  
  
 A. Model nie publiczny dostawca jest dostępny. W tej chwili [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje program SQL Server i [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)] tylko.  
  
## <a name="sql-injection-attacks"></a>Ataki polegające na iniekcji SQL  
 PYTANIE: Jak jest [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] chronione przed atakami polegającymi na iniekcji SQL?  
  
 A. Wstrzyknięcie kodu SQL została znaczne ryzyko dla tradycyjnych zapytania SQL, utworzone przez złączenie dane wejściowe użytkownika. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pozwala uniknąć takich iniekcji przy użyciu <xref:System.Data.SqlClient.SqlParameter> w zapytaniach. Dane wejściowe użytkownika jest przekształcane w wartości parametrów. To podejście zapobiega szkodliwe polecenia używana z klienta w danych wejściowych.  
  
## <a name="changing-read-only-flag-in-dbml-files"></a>Zmiana flagi tylko do odczytu w DBML, pliki  
 PYTANIE: Jak wyeliminować metod ustawiających z niektórych właściwości, podczas tworzenia modelu obiektu pliku DBML?  
  
 A. Wykonaj następujące kroki w tym scenariuszu zaawansowane:  
  
1. W pliku dbml, należy zmodyfikować właściwość, zmieniając <xref:System.Data.Linq.ITable.IsReadOnly%2A> flaga `True`.  
  
2. Dodaj klasę częściową. Utwórz konstruktora z parametrami dla członków z prawami tylko do odczytu.  
  
3. Przejrzyj domyślne <xref:System.Data.Linq.Mapping.UpdateCheck> wartość (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) aby określić, czy jest poprawny dla twojej aplikacji.  
  
    > [!CAUTION]
    >  Jeśli używasz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] w programie Visual Studio, Twoje zmiany mogą być zastępowane.  
  
## <a name="aptca"></a>APTCA  
 PYTANIE: System.Data.Linq oznaczono do użycia przez częściowo zaufany kod?  
  
 A. Tak, to zestaw System.Data.Linq.dll wśród tych zestawów .NET Framework, oznaczone <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu. Bez tego oznaczania zestawy .NET Framework są przeznaczone do użytku tylko przez w pełni zaufany kod.  
  
 Główna scenariusza w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dla umożliwiając częściowo zaufanych obiektów wywołujących jest umożliwienie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zestawu można uzyskać dostęp z aplikacji sieci Web, gdzie *zaufania* konfiguracji to średni.  
  
## <a name="mapping-data-from-multiple-tables"></a>Mapowanie danych z wielu tabel  
 PYTANIE: Dane w jednostce Moje pochodzą z wielu tabel. Sposób mapowania go  
  
 A. Można utworzyć widok w bazie danych i mapowania jednostki do widoku. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje ten sam SQL dla widoków, jak w przypadku tabel.  
  
> [!NOTE]
>  Korzystanie z widoków, w tym scenariuszu ma ograniczenia. To podejście pozwala skutecznie najbezpieczniejszy, gdy operacje wykonywane na <xref:System.Data.Linq.Table%601> są obsługiwane w bazowym widoku. Tylko wiesz, jakie operacje są przeznaczone. Na przykład większość aplikacji są przeznaczone tylko do odczytu i wykonania innego znaczną liczbę `Create` / `Update` / `Delete` operacji tylko przy użyciu przechowywanych procedur w odniesieniu do widoków.  
  
## <a name="connection-pooling"></a>Pula połączeń  
 PYTANIE: Czy istnieje konstrukcja, która może ułatwić <xref:System.Data.Linq.DataContext> puli?  
  
 A. Nie próbuj ponownie użyć wystąpienia <xref:System.Data.Linq.DataContext>. Każdy <xref:System.Data.Linq.DataContext> obsługuje stan (łącznie z pamięci podręcznej tożsamości) dla jednej sesji edycji/kwerendy. Aby uzyskać nowe wystąpienia, w oparciu o bieżący stan bazy danych, użyj nowego <xref:System.Data.Linq.DataContext>.  
  
 Można nadal używać bazowych [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] buforowania połączeń. Aby uzyskać więcej informacji, zobacz [programu SQL Server połączenia puli (ADO.NET)](../../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
## <a name="second-datacontext-is-not-updated"></a>Drugi element DataContext nie jest aktualizowana.  
 PYTANIE: Czy mogę używać jedno wystąpienie <xref:System.Data.Linq.DataContext> do przechowywania wartości w bazie danych. Jednak sekundy <xref:System.Data.Linq.DataContext> na tej samej bazy danych nie będzie odzwierciedlał zaktualizowanymi wartościami. Drugi <xref:System.Data.Linq.DataContext> wystąpienia wydaje się, że zwracane wartości pamięci podręcznej.  
  
 A. To zachowanie jest celowe. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] w dalszym ciągu zwracane tego samego wystąpienia/wartości, które widać w pierwszej kolejności. Po wprowadzeniu aktualizacji, możesz użyć optymistycznej współbieżności. Oryginalnych danych służy do sprawdzania z bieżącym stanem bazy danych do potwierdzenia, że w rzeczywistości nadal jest bez zmian. Jeśli została ona zmieniona występuje konflikt, i aplikacji należy go rozwiązać. Jedną z opcji aplikacji jest, aby przywrócić oryginalny stan bieżący stan bazy danych i ponowienie próby aktualizacji. Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
 Można również ustawić <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> na wartość false, która włącza wyłączone buforowanie i śledzenie zmian. Najnowsze wartości można później odzyskać za każdym razem, które można zbadać.  
  
## <a name="cannot-call-submitchanges-in-read-only-mode"></a>Nie można wywołać SubmitChanges w trybie tylko do odczytu  
 PYTANIE: Podczas próby wywołania <xref:System.Data.Linq.DataContext.SubmitChanges%2A> w trybie tylko do odczytu, pojawia się błąd.  
  
 A. Tryb tylko do odczytu wyłącza możliwość śledzenia zmian kontekstu.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [Rozwiązywanie problemów](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)
- [Zabezpieczenia w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md)
