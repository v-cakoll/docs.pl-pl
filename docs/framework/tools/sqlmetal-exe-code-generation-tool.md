---
title: SqlMetal.exe (Narzędzie generowania kodu)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
caps.latest.revision: 43
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5c21c08cf76143959d11498594fbc94fb1dac55c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="sqlmetalexe-code-generation-tool"></a>SqlMetal.exe (Narzędzie generowania kodu)
Narzędzie wiersza polecenia SqlMetal generuje kod i mapowania dla [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] składnika [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Stosując opisane w dalszej części tego tematu opcje, można za pomocą programu SqlMetal wykonać kilka różnych akcji, takich jak:  
  
-   Na podstawie bazy danych — generowanie kodu źródłowego i atrybutów mapowania lub pliku mapowania.  
  
-   Na podstawie bazy danych — generowanie pliku języka Intermediate Database Markup Language (dbml) na potrzeby dostosowywania.  
  
-   Na podstawie pliku dbml — generowanie kodu i atrybutów mapowania lub pliku mapowania.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Domyślnie plik znajduje się w `drive`: \Program Files\Microsoft SDKs\Windows\v`n.nn`\bin. Jeśli nie zostanie zainstalowany program Visual Studio, można także uzyskać plik SQLMetal, pobierając [zestaw Windows SDK](http://go.microsoft.com/fwlink/?LinkId=142225).  
  
> [!NOTE]
>  Deweloperzy korzystający z programu Visual Studio umożliwia również [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] można wygenerować klas jednostek. Podejście z użyciem wiersza polecenia dobrze sprawdza się w przypadku dużych baz danych. Program SqlMetal to narzędzie wiersza polecenia, więc można użyć go w procesie kompilacji.  
  
 Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md). W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a>Opcje  
 Aby wyświetlić najbardziej aktualną listę opcji, należy wpisać `sqlmetal /?` w wierszu polecenia z zainstalowanych lokalizacji.  
  
 **Opcje połączenia**  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/ Server:**  *\<name >*|Określa nazwę serwera bazy danych.|  
|**/ bazy danych:**  *\<name >*|Określa wykaz baz danych na serwerze.|  
|**/ User:**  *\<name >*|Określa identyfikator logowania użytkownika. Wartość domyślna: Użyj uwierzytelniania systemu Windows.|  
|**/ password:**  *\<hasło >*|Określa hasło logowania. Wartość domyślna: Użyj uwierzytelniania systemu Windows.|  
|**/ conn:**  *\<ciąg połączenia >*|Określa parametry połączenia z bazą danych. Nie można używać z **/Server**, **/bazy danych**, **User**, lub **/Password** opcje.<br /><br /> W parametrach połączenia nie można umieszczać nazwy pliku. Zamiast tego należy określić nazwę pliku w wierszu polecenia jako plik wejściowy. Na przykład poniższy wiersz określa "c:\northwnd.mdf" jako pliku wejściowego: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.|  
|**/ timeout:**  *\<sekund >*|Określa wartość limitu czasu używaną, gdy program SqlMetal uzyskuje dostęp do bazy danych. Wartość domyślna: 0 (czyli brak limitu czasu).|  
  
 **Opcje wyodrębniania**  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/views**|Wyodrębnia widoki bazy danych.|  
|**/Functions**|Wyodrębnia funkcje bazy danych.|  
|**/sprocs**|Wyodrębnia procedury składowane.|  
  
 **Opcje wyjściowe**  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/dbml** *[: plik]*|Wysyła dane wyjściowe w postaci pliku dbml. Nie można używać z **/map** opcji.|  
|**/ Kod** *[: plik]*|Wysyła dane wyjściowe w postaci kodu źródłowego. Nie można używać z **/dbml** opcji.|  
|**/ map** *[: plik]*|Generuje plik mapowania XML zamiast atrybutów. Nie można używać z **/dbml** opcji.|  
  
 **Różne**  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/Language:**  *\<języka >*|Określa język kodu źródłowego.<br /><br /> Nieprawidłowa  *\<języka >*: vb, csharp.<br /><br /> Wartość domyślna: pochodzi z rozszerzeniem nazwy pliku kodu.|  
|**/ NAMESPACE:**  *\<name >*|Określa przestrzeń nazw wygenerowanego kodu. Wartość domyślna: brak przestrzeni nazw.|  
|**/ Context:**  *\<typu >*|Określa nazwę klasy kontekstu danych. Wartość domyślna: pochodzi z nazwy bazy danych.|  
|**/entitybase:**  *\<typu >*|Określa klasę bazową klas obiektów w generowanym kodzie. Wartość domyślna: obiekty nie mają klasy bazowej.|  
|**/ pluralize**|Automatycznie zmienia nazwy klas i składowych na liczbę mnogą lub pojedynczą.<br /><br /> Ta opcja jest dostępna tylko w Stanach Zjednoczonych Wersja w języku angielskim.|  
|**/Serialization:**  *\<opcji >*|Generuje klasy, które można serializować.<br /><br /> Nieprawidłowa  *\<opcji >*: Brak Unidirectional. Wartość domyślna: None.<br /><br /> Aby uzyskać więcej informacji, zobacz [szeregowanie](../../../docs/framework/data/adonet/sql/linq/serialization.md).|  
  
 **Plik wejściowy**  
  
|Opcja|Opis|  
|------------|-----------------|  
|**\<Plik wejściowy >**|Określa plik .mdf programu SQL Server Express [!INCLUDE[ssEW](../../../includes/ssew-md.md)] pliku .sdf lub .dbml pliku pośredniego.|  
  
## <a name="remarks"></a>Uwagi  
 Działanie programu SqlMetal w rzeczywistości obejmuje wykonanie dwóch kroków:  
  
-   Wyodrębnienie metadanych bazy danych do pliku dbml.  
  
-   Wygenerowanie pliku wyjściowego z kodem.  
  
     Za pomocą odpowiednich opcji wiersza polecenia, można utworzyć kodu źródłowego języka Visual Basic lub C#, lub można utworzyć mapowania pliku XML.  
  
 Aby wyodrębnić metadane z pliku mdf, należy określić nazwę pliku mdf po wszystkich innych opcjach.  
  
 Jeśli nie **/Server** jest określony, **localhost/sqlexpress** zakłada, że.  
  
 [!INCLUDE[sqprsqext](../../../includes/sqprsqext-md.md)] zgłasza wyjątek, jeśli spełnione są co najmniej jeden z następujących warunków:  
  
-   Program SqlMetal próbuje wyodrębnić procedurę składowaną, którą sam wywołuje.  
  
-   Poziom zagnieżdżenia procedury składowanej, funkcji lub widoku przekracza 32.  
  
     Program SqlMetal przechwytuje ten wyjątek i zgłasza go jako ostrzeżenie.  
  
 Aby określić nazwę pliku wejściowego, należy dodać ją do wiersza polecenia jako plik wejściowy. Łącznie z nazwą pliku w ciągu połączenia (przy użyciu **/conn** opcji) nie jest obsługiwana.  
  
## <a name="examples"></a>Przykłady  
 Generuje plik dbml zawierający wyodrębnione metadane SQL:  
  
 **sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**  
  
 Generuje plik dbml zawierający metadane SQL wyodrębnione z pliku mdf przy użyciu programu SQL Server Express:  
  
 **sqlmetal /dbml:mymeta.dbml mydbfile.mdf**  
  
 Generuje plik dbml zawierający metadane SQL wyodrębnione z programu SQL Server Express:  
  
 **sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**  
  
 Generuje kod źródłowy na podstawie pliku metadanych dbml:  
  
 **sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**  
  
 Generuje kod źródłowy bezpośrednio na podstawie metadanych SQL:  
  
 **sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**  
  
> [!NOTE]
>  Jeśli używasz **/ pluralize** opcję z przykładowej bazy danych Northwind, należy pamiętać o następujących zasadach. Gdy program SqlMetal tworzy nazwy tabel typu wiersz, nazwy tabel mają liczbę pojedynczą. Gdy ułatwia <xref:System.Data.Linq.DataContext> właściwości dla tabel, nazwy tabeli są liczbie mnogiej. Przypadkowo nazwy tabel w przykładowej bazie danych Northwind mają już liczbę mnogą. Dlatego też nie widać działania tej części opcji. Popularną praktyką jest nadawanie tabelom w bazie danych nazw w liczbie pojedynczej, ale równie popularną praktyką na platformie .NET jest nadawanie kolekcjom nazw w liczbie mnogiej.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Generowanie modelu obiektu w języku Visual Basic lub C#](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 [Generowanie kodu w składniku LINQ to SQL](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [Mapowanie zewnętrzne](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
