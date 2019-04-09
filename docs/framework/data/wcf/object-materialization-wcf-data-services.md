---
title: Materializacja obiektu (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
ms.openlocfilehash: c63dd07686463c652c27dea8473b4d8cbe2dab71
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137673"
---
# <a name="object-materialization-wcf-data-services"></a>Materializacja obiektu (WCF Data Services)
Kiedy używasz **Dodaj odwołanie do usługi** okno dialogowe, aby używać [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych w aplikacji klienta opartego na programie .NET Framework, klas danych równoważne są generowane dla każdego typu jednostki w modelu danych udostępnianych przez źródło danych. Aby uzyskać więcej informacji, zobacz [Generowanie biblioteki klienta usługi danych](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md). Jednostki danych zwracanych przez zapytanie jest zmaterializowany do wystąpienia jednego z tych klas usługi danych wygenerowanego klienta. Aby uzyskać informacji na temat opcji scalania i rozwiązanie tożsamości dla śledzonych obiektów, zobacz [zarządzanie kontekstem usługi danych](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umożliwia także zdefiniować własne klas usługi danych klienta, a nie przy użyciu klas danych generowanych przez narzędzie. Dzięki temu można użyć własnych klas danych, nazywane również "old zwykłego obiektu CLR" klas danych (POCO). Korzystając z tych typów danych niestandardowych klas, powinien atrybutu klasy danych z oboma <xref:System.Data.Services.Common.DataServiceKeyAttribute> lub <xref:System.Data.Services.Common.DataServiceEntityAttribute> i upewnij się, że typ nazwy o nazwach klienta dopasowanie typu w modelu danych usługi danych.  
  
 Gdy biblioteka otrzyma komunikat odpowiedzi zapytania, go materializuje dane zwrócone z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych do wystąpień danych klienta, klas usług, które są typu zapytania. Ogólny proces materializowanie tych obiektów, jest następujący:  
  
1.  Biblioteka klienta odczytuje typu serializacji z `entry` element komunikat odpowiedzi z kanału informacyjnego i próbuje utworzyć nowe wystąpienie poprawnego typu w jednym z następujących sposobów:  
  
    -   Gdy typ zadeklarowany w źródle danych ma taką samą nazwę jak typ <xref:System.Data.Services.Client.DataServiceQuery%601>, nowe wystąpienie tego typu jest tworzona przy użyciu pustego konstruktora.  
  
    -   Gdy typ zadeklarowany w źródle danych ma taką samą nazwę jak typ, który jest tworzony na podstawie typu <xref:System.Data.Services.Client.DataServiceQuery%601>, nowe wystąpienie tego typu pochodnego jest tworzona przy użyciu pustego konstruktora.  
  
    -   Gdy typ zadeklarowany w źródle danych nie można dopasować do typu <xref:System.Data.Services.Client.DataServiceQuery%601> lub dowolne typy pochodne, nowe wystąpienie typu kwerendy jest tworzona przy użyciu pustego konstruktora.  
  
    -   Gdy <xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A> właściwość jest ustawiona, podane delegata jest wywoływana, aby zastąpić domyślne mapowanie na podstawie nazwy typu i nowe wystąpienie klasy typ zwracany przez <xref:System.Func%602> zostanie utworzona. Jeśli ten delegat zwraca wartość null, tworzone jest nowe wystąpienie, typu kwerendy. Może być wymagane do zastąpienia domyślnego mapowania nazwy na podstawie nazwy typu do obsługi scenariuszy dziedziczenia.  
  
2.  Biblioteka klienta odczytuje wartość identyfikatora URI z `id` elementu `entry`, czyli wartość tożsamości podmiotu. Chyba że <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> wartość <xref:System.Data.Services.Client.MergeOption.NoTracking> jest używany, wartość tożsamości jest używane do śledzenia obiektu w <xref:System.Data.Services.Client.DataServiceContext>. Wartość tożsamości umożliwia również zagwarantować, że tylko pojedynczy element tworzone jest wystąpienie, nawet wtedy, gdy jednostki są zwracane wielokrotnie w odpowiedzi na zapytanie.  
  
3.  Biblioteka klienta odczytuje właściwości z kanału informacyjnego wpisu i ustaw odpowiednie właściwości nowo utworzony obiekt. Jeśli obiekt, który ma taką samą wartość tożsamość, już występuje w <xref:System.Data.Services.Client.DataServiceContext>, właściwości są ustawione na podstawie <xref:System.Data.Services.Client.MergeOption> ustawienie <xref:System.Data.Services.Client.DataServiceContext>. Odpowiedź może zawierać wartości właściwości, dla których odpowiadającą właściwość nie występuje w typ klienta. W takiej sytuacji działania zależą od wartości <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> właściwość <xref:System.Data.Services.Client.DataServiceContext>. Jeśli ta właściwość jest równa `true`, brakująca właściwość jest ignorowana. W przeciwnym wypadku zgłaszany jest błąd. Właściwości są ustawione w następujący sposób:  
  
    -   Właściwości skalarne są ustawione na wartość odpowiadająca we wpisie w komunikacie odpowiedzi.  
  
    -   Złożonych właściwości można ustawić nowe wystąpienie typu złożonego, które są konfigurowane przy użyciu właściwości typu złożonego z odpowiedzi.  
  
    -   Właściwości nawigacji, które zwracają zbiór powiązanych jednostek są ustawiane w ramach nowego lub istniejącego wystąpienia <xref:System.Collections.Generic.ICollection%601>, gdzie `T` jest typem powiązanej jednostki. Ta kolekcja jest pusta, chyba że powiązane obiekty zostały załadowane do <xref:System.Data.Services.Client.DataServiceContext>. Aby uzyskać więcej informacji, zobacz [ładowanie zawartości odroczone](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
        > [!NOTE]
        >  Gdy klas danych wygenerowanego klienta obsługuje powiązanie danych, właściwości nawigacji zwrócić wystąpienia <xref:System.Data.Services.Client.DataServiceCollection%601> klasy zamiast tego. Aby uzyskać więcej informacji, zobacz [powiązanie danych z kontrolkami](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
4.  <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity> Zdarzenie jest wywoływane.  
  
5.  Biblioteka klienta dołącza obiekt do <xref:System.Data.Services.Client.DataServiceContext>. Obiekt nie jest dołączony, kiedy <xref:System.Data.Services.Client.MergeOption> jest <xref:System.Data.Services.Client.MergeOption.NoTracking>.  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie zapytań do usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
- [Projekcje zapytania](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)
