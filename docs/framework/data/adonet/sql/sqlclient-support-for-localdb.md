---
title: Obsługa SqlClient w bazie danych LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: d02524cd5901adeca7bc36d6fd13c7abdc46c69b
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894401"
---
# <a name="sqlclient-support-for-localdb"></a>Obsługa SqlClient w bazie danych LocalDB
Począwszy od SQL Server nazwy Denali, zostanie udostępniona uproszczona wersja SQL Server o nazwie LocalDB. W tym temacie omówiono sposób nawiązywania połączenia z bazą danych LocalDB.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat LocalDB, w tym sposobu instalowania LocalDB i konfigurowania wystąpienia LocalDB, zobacz SQL Server Books Online.  
  
 Aby podsumować, co możesz zrobić z LocalDB:  
  
- Twórz i uruchamiaj wystąpienia LocalDB za pomocą SqlLocalDB. exe lub pliku App. config.  
  
- Użyj narzędzia sqlcmd. exe do dodawania i modyfikowania baz danych w wystąpieniu LocalDB. Na przykład `sqlcmd -S (localdb)\myinst`.  
  
- Użyj słowa `AttachDBFilename` kluczowego Connection, aby dodać bazę danych do wystąpienia usługi LocalDB. Jeśli używasz `AttachDBFilename`, jeśli nie określisz nazwy bazy danych `Database` za pomocą słowa kluczowego Connection, baza danych zostanie usunięta z wystąpienia LocalDB, gdy aplikacja zostanie zamknięta.  
  
- Określ wystąpienie LocalDB w parametrach połączenia. Na przykład nazwa wystąpienia to `myInstance`, ciąg połączenia:  
  
    `server=(localdb)\\myInstance`  
  
 `User Instance=True`nie jest dozwolone podczas nawiązywania połączenia z bazą danych LocalDB.  
  
 Możesz pobrać LocalDB z [pakietu Feature Pack Microsoft SQL Server 2012](https://www.microsoft.com/download/en/details.aspx?id=29065). Jeśli użyjesz narzędzia sqlcmd. exe do modyfikacji danych w wystąpieniu usługi LocalDB, będziesz potrzebować narzędzia sqlcmd z SQL Server 2012, które można również uzyskać z pakietu SQL Server 2012 Feature Pack.  
  
## <a name="programmatically-create-a-named-instance"></a>Programowe tworzenie nazwanego wystąpienia  
 Aplikacja może utworzyć nazwane wystąpienie i określić bazę danych w następujący sposób:  
  
- Określ wystąpienia LocalDB do utworzenia w pliku App. config w następujący sposób.  Numer wersji wystąpienia powinien być taki sam jak numer wersji instalacji programu LocalDB.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <configSections>  
        <section  
        name="system.data.localdb"  
        type="System.Data.LocalDBConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>  
      </configSections>  
      <system.data.localdb>  
        <localdbinstances>  
          <add name="myInstance" version="11.0" />  
        </localdbinstances>  
      </system.data.localdb>  
    </configuration>  
    ```  
  
- Określ nazwę wystąpienia za pomocą `server` słowa kluczowego parametrów połączenia.  Nazwa wystąpienia określona w `server` słowie kluczowym parametrów połączenia musi być zgodna z nazwą określoną w pliku App. config.  
  
- Użyj słowa `AttachDBFilename` kluczowego Connection, aby określić. Plik MDF.  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje Serwera SQL i ADO.NET](sql-server-features-and-adonet.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
