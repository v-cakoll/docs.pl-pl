---
title: Obsługa SqlClient w bazie danych LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 23fe0d19ad31c0b09e1a12b5ea25e45a973a14f4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645830"
---
# <a name="sqlclient-support-for-localdb"></a>Obsługa SqlClient w bazie danych LocalDB
Począwszy od programu SQL Server o nazwie kodowej Denali Uproszczona wersja programu SQL Server, o nazwie LocalDB, będą dostępne. W tym temacie omówiono sposób nawiązywania połączeń z bazą danych LocalDB.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji dotyczących programu LocalDB, na przykład zainstaluj LocalDB i skonfiguruj wystąpienia LocalDB zobacz dokumentację SQL Server — książki Online.  
  
 Aby podsumować, co można zrobić z bazą danych LocalDB:  
  
- Tworzenie i uruchamianie wystąpienia LocalDB sqllocaldb.exe lub pliku app.config.  
  
- Użyj programu sqlcmd.exe, aby dodawać i modyfikować baz danych w wystąpieniu LocalDB. Na przykład `sqlcmd -S (localdb)\myinst`.  
  
- Użyj `AttachDBFilename` słowo kluczowe parametrów połączenia, aby dodać bazę danych do wystąpienia LocalDB. Korzystając z `AttachDBFilename`, jeśli nie określisz nazwę bazy danych za pomocą `Database` słowo kluczowe parametrów połączenia bazy danych zostaną usunięte z wystąpienia LocalDB po zamknięciu aplikacji.  
  
- Określ wystąpienie programu LocalDB w ciągu połączenia. Na przykład, Twoja nazwa wystąpienia jest `myInstance`, obejmują parametry połączenia:  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 `User Instance=True` nie jest dozwolone podczas nawiązywania połączenia z bazą danych LocalDB.  
  
 Możesz pobrać LocalDB z [programu Microsoft SQL Server 2012 Feature Pack](https://www.microsoft.com/download/en/details.aspx?id=29065). Jeśli sqlcmd.exe będzie używać do modyfikacji danych w ramach wystąpienia LocalDB, konieczne będzie sqlcmd z programu SQL Server 2012, którą możesz również pobrać z programu SQL Server 2012 Feature Pack.  
  
## <a name="programmatically-create-a-named-instance"></a>Programowe tworzenie nazwanego wystąpienia  
 Aplikację można utworzenia nazwanego wystąpienia i Określ bazę danych, w następujący sposób:  
  
- Określ wystąpienia LocalDB do tworzenia w pliku app.config, w następujący sposób.  Numer wersji wystąpienia powinien być taki sam jak numer wersji instalacji programu LocalDB.  
  
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
  
- Określ nazwę wystąpienia przy użyciu `server` słowo kluczowe parametrów połączenia.  Nazwa wystąpienia określonego w `server` słowo kluczowe parametrów połączenia musi pasować do nazwy określonej w pliku app.config.  
  
- Użyj `AttachDBFilename` słowo kluczowe parametrów połączenia, aby określić. Plik MDF.  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje Serwera SQL i ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
