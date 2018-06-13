---
title: Obsługa SqlClient LocalDB
ms.date: 03/30/2017
ms.assetid: cf796898-5575-46f2-ae6e-21e5aa8c4123
ms.openlocfilehash: 33368ca4b2dc5397087d29e515db6c1094e350bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359800"
---
# <a name="sqlclient-support-for-localdb"></a>Obsługa SqlClient LocalDB
Począwszy od programu SQL Server o nazwie kodowej Denali to Uproszczona wersja programu SQL Server o nazwie LocalDB, będą dostępne. W tym temacie omówiono sposób nawiązywania połączenia z bazą danych LocalDB.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat LocalDB, łącznie ze sposobem LocalDB zainstalować i skonfigurować wystąpienie bazy danych LocalDB zobacz dokumentację SQL Server — książki Online.  
  
 Podsumowując, co można zrobić LocalDB:  
  
-   Utwórz i uruchom wystąpień LocalDB sqllocaldb.exe lub pliku app.config.  
  
-   Użyj programu sqlcmd.exe, aby dodawać i modyfikować baz danych w wystąpieniu bazy danych LocalDB. Na przykład `sqlcmd -S (localdb)\myinst`.  
  
-   Użyj `AttachDBFilename` słowo kluczowe parametrów połączenia, aby dodać bazy danych do wystąpienia bazy danych LocalDB. Korzystając z `AttachDBFilename`, jeśli nie określisz nazwy bazy danych z `Database` słowo kluczowe parametrów połączenia bazy danych zostaną usunięte z wystąpieniem LocalDB po zamknięciu aplikacji.  
  
-   Określ wystąpienie bazy danych LocalDB w ciągu połączenia. Na przykład Twoja nazwa wystąpienia jest `myInstance`, to ciąg połączenia:  
  
    ```  
    server=(localdb)\\myInstance  
    ```  
  
 `User Instance=True` nie jest dozwolona podczas nawiązywania połączenia z bazą danych LocalDB.  
  
 Możesz pobrać LocalDB z [Microsoft SQL Server 2012 Feature Pack](http://www.microsoft.com/download/en/details.aspx?id=29065). Jeśli użyjesz sqlcmd.exe, aby modyfikować danych w wystąpieniu bazy danych LocalDB, konieczne będzie sqlcmd z programu SQL Server 2012, który możesz również pobrać ze strony programu SQL Server 2012 Feature Pack.  
  
## <a name="programmatically-create-a-named-instance"></a>Programowe tworzenie wystąpienia nazwanego  
 Aplikację można utworzyć wystąpienia nazwanego i Określ bazę danych, w następujący sposób:  
  
-   Określ wystąpienia bazy danych LocalDB, utworzenie w pliku app.config, w następujący sposób.  Numer wersji wystąpienia powinien być taki sam jak numer wersji instalacji bazy danych LocalDB programu.  
  
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
  
-   Określ nazwę wystąpienia, przy użyciu `server` słowo kluczowe parametrów połączenia.  Podana nazwa wystąpienia w `server` słowo kluczowe parametrów połączenia musi pasować do nazwy określonej w pliku app.config.  
  
-   Użyj `AttachDBFilename` słowo kluczowe parametrów połączenia, aby określić. Pliku MDF.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje Serwera SQL i ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
