---
title: Obiekt Materialization (usługi danych WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
ms.openlocfilehash: 54f8cc876b373fcfa8e8e514abf50111942de88c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="object-materialization-wcf-data-services"></a>Obiekt Materialization (usługi danych WCF)
Jeśli używasz **Dodaj odwołanie do usługi** okna dialogowego, aby korzystać z [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych w aplikacji klienta opartego na programie .NET Framework, dane równoważne klasy są generowane dla poszczególnych typów jednostek w modelu danych udostępnianych przez źródło. Aby uzyskać więcej informacji, zobacz [generowania biblioteki klienta usługi danych](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md). Jednostka danych zwracanych przez zapytanie jest zmaterializowany do wystąpienia jednego z tych klas usług danych wygenerowanego klienta. Uzyskać informacji o opcji scalania i rozpoznawania tożsamości dla śledzonych obiektów, zobacz [Zarządzanie kontekstu danych usługi](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umożliwia definiowanie własnych klas usług danych klienta, a nie przy użyciu klasy dane generowane przez narzędzie. Dzięki temu można użyć własnych klas danych, nazywane również "starego zwykłego obiektu CLR" klas danych (POCO). Korzystając z tych typów danych niestandardowych klas, powinien atrybutu klasy danych przy użyciu jednej <xref:System.Data.Services.Common.DataServiceKeyAttribute> lub <xref:System.Data.Services.Common.DataServiceEntityAttribute> i upewnij się, że typ nazwy na nazwy typu dopasowania klienta usługi danych modelu danych.  
  
 Gdy biblioteki otrzyma komunikat odpowiedzi zapytania, zostaje on zwrócone dane z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych do wystąpień danych klienta klasy usługi, które są właściwościami typu zapytania. Ogólny proces materializowania tych obiektów jest następujący:  
  
1.  Biblioteka klienta odczytuje typu serializacji z `entry` element w źródła komunikatu odpowiedzi i próbuje utworzyć nowe wystąpienie klasy poprawny typ, w jednym z następujących sposobów:  
  
    -   Jeśli typ zadeklarowany w źródle danych ma taką samą nazwę jak typ <xref:System.Data.Services.Client.DataServiceQuery%601>, nowe wystąpienie klasy tego typu jest tworzona przy użyciu pustego konstruktora.  
  
    -   Jeśli typ zadeklarowany w źródle danych ma taką samą nazwę jak typ, który pochodzi od typu <xref:System.Data.Services.Client.DataServiceQuery%601>, nowe wystąpienie klasy tego typu pochodnego jest tworzona przy użyciu pustego konstruktora.  
  
    -   Jeśli typ zadeklarowany w źródle danych nie można dopasować do typu <xref:System.Data.Services.Client.DataServiceQuery%601> lub dowolne typy pochodne, nowe wystąpienie, którego dotyczy kwerenda typu jest tworzona przy użyciu pustego konstruktora.  
  
    -   Gdy <xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A> właściwość jest ustawiona, dostarczony delegat jest wywoływana, aby zastąpić domyślne mapowanie typu na podstawie nazwy i nowe wystąpienie klasy typ zwracany przez <xref:System.Func%602> zostanie utworzona. Jeśli ten delegat zwraca wartość null, zostanie utworzona nowe wystąpienie typu, którego dotyczy kwerenda. Może być wymagane do zastępowania domyślnego mapowania nazwy na podstawie nazwy typu na potrzeby obsługi scenariuszy dziedziczenia.  
  
2.  Biblioteka klienta odczytuje wartość identyfikatora URI z `id` elementu `entry`, czyli wartość tożsamości jednostki. O ile <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> wartość <xref:System.Data.Services.Client.MergeOption.NoTracking> jest używany, wartość tożsamości służy do śledzenia obiektów w <xref:System.Data.Services.Client.DataServiceContext>. Wartość tożsamości służy również do zagwarantowania, że tylko pojedynczy element jest tworzone wystąpienie, nawet wtedy, gdy obiekt jest zwracany wiele razy w odpowiedzi na kwerendę.  
  
3.  Biblioteka klienta odczytuje właściwości z wpisu źródła i ustaw odpowiednie właściwości dla nowo utworzony obiekt. Po wystąpieniu obiektu, który już ma taką samą wartość identity w <xref:System.Data.Services.Client.DataServiceContext>, właściwości są ustawione na podstawie <xref:System.Data.Services.Client.MergeOption> ustawienie <xref:System.Data.Services.Client.DataServiceContext>. Odpowiedzi mogą zawierać wartości właściwości, dla których odpowiadającej właściwości nie występuje w typ klienta. W takim przypadku akcji zależy od wartości <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> właściwość <xref:System.Data.Services.Client.DataServiceContext>. Jeśli ta właściwość jest równa `true`, brak właściwość jest ignorowana. W przeciwnym razie błąd. Właściwości są ustawione w następujący sposób:  
  
    -   Właściwości skalarne są ustawione na wartość odpowiadająca we wpisie w komunikacie odpowiedzi.  
  
    -   Złożone są ustawione właściwości do nowego wystąpienia typu złożonego, które są konfigurowane przy użyciu właściwości typu złożonego z odpowiedzi.  
  
    -   Właściwości nawigacji, które zwraca kolekcję obiektów powiązane są ustawione do nowego lub istniejącego wystąpienia programu <xref:System.Collections.Generic.ICollection%601>, gdzie `T` jest typem obiektu pokrewnego. Ta kolekcja jest pusta, chyba że powiązane obiekty zostały załadowane do <xref:System.Data.Services.Client.DataServiceContext>. Aby uzyskać więcej informacji, zobacz [ładowanie odłożone zawartości](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
        > [!NOTE]
        >  Gdy klas danych wygenerowanego klienta obsługuje powiązanie danych, właściwości nawigacji zwrócić wystąpienia <xref:System.Data.Services.Client.DataServiceCollection%601> zamiast klasy. Aby uzyskać więcej informacji, zobacz [wiązanie danych do kontrolek](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
4.  <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity> Zdarzenia.  
  
5.  Biblioteka klienta dołącza obiektu <xref:System.Data.Services.Client.DataServiceContext>. Obiekt nie jest dołączony, kiedy <xref:System.Data.Services.Client.MergeOption> jest <xref:System.Data.Services.Client.MergeOption.NoTracking>.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykonywanie zapytań do usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 [Projekcje zapytania](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)
