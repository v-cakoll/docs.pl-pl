---
title: Obiekt materializację (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
ms.assetid: f0dbf7b0-0292-4e31-9ae4-b98288336dc1
ms.openlocfilehash: d45d472a2996c0b501af70a0a2a6d2d669dedb4d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043535"
---
# <a name="object-materialization-wcf-data-services"></a>Obiekt materializację (Usługi danych programu WCF)

W przypadku korzystania z okna dialogowego **Dodaj odwołanie do usługi** do korzystania [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] z kanału informacyjnego w aplikacji klienckiej opartej na .NET Framework są generowane równoważne klasy danych dla każdego typu jednostki w modelu danych udostępnionym przez kanał informacyjny. Aby uzyskać więcej informacji, zobacz [generowanie biblioteki klienta usługi danych](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md). Dane jednostki, które są zwracane przez zapytanie, są uwzględniane w wystąpieniu jednej z wygenerowanych klas usługi danych klienta. Aby uzyskać informacje na temat opcji scalania i rozpoznawania tożsamości dla śledzonych obiektów, zobacz [zarządzanie kontekstem usługi danych](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md).

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umożliwia także Definiowanie własnych klas usługi danych klienta zamiast używać klas danych generowanych przez narzędzie. Umożliwia to korzystanie z własnych klas danych, nazywanych również "zwykłymi klasami danych CLR" (POCO). W przypadku korzystania z tych typów niestandardowych klas danych należy przypisać klasę danych z <xref:System.Data.Services.Common.DataServiceKeyAttribute> lub <xref:System.Data.Services.Common.DataServiceEntityAttribute> i upewnić się, że nazwy typów na klientach są zgodne z nazwami typów w modelu danych usługi danych.

Gdy biblioteka otrzyma komunikat odpowiedzi na zapytanie, materializuje zwrócone dane ze [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych do wystąpień klas usługi danych klienta, które są typu zapytania. Ogólny proces materializacji tych obiektów jest następujący:

1. Biblioteka kliencka odczytuje Zserializowany typ z `entry` elementu w kanale informacyjnym komunikatu odpowiedzi i próbuje utworzyć nowe wystąpienie poprawnego typu w jeden z następujących sposobów:

    - Gdy typ zadeklarowany w kanale informacyjnym ma taką samą nazwę jak typ <xref:System.Data.Services.Client.DataServiceQuery%601>, nowe wystąpienie tego typu jest tworzone za pomocą pustego konstruktora.

    - Gdy typ zadeklarowany w źródle danych ma taką samą nazwę jak typ, który pochodzi od typu <xref:System.Data.Services.Client.DataServiceQuery%601>, nowe wystąpienie tego typu pochodnego jest tworzone za pomocą pustego konstruktora.

    - Gdy typ zadeklarowany w kanale informacyjnym nie może być dopasowany do <xref:System.Data.Services.Client.DataServiceQuery%601> typu lub dowolnego typu pochodnego, nowe wystąpienie typu zapytania jest tworzone za pomocą pustego konstruktora.

    - Gdy właściwość jest ustawiona, dostarczony delegat jest wywoływany w celu przesłania domyślnego mapowania typu opartego na nazwie i nowego wystąpienia typu zwracanego <xref:System.Func%602> przez. <xref:System.Data.Services.Client.DataServiceContext.ResolveType%2A> Jeśli delegat zwraca wartość null, zamiast tego zostanie utworzone nowe wystąpienie typu zapytania. Może być wymagane przesłonięcie domyślnego mapowania nazw typów opartych na nazwach w celu obsługi scenariuszy dziedziczenia.

2. Biblioteka kliencka odczytuje wartość identyfikatora URI z `id` elementu `entry`, który jest wartością tożsamości jednostki. <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> Jeśli <xref:System.Data.Services.Client.DataServiceContext>wartość nie jest używana, wartość tożsamości służy do śledzenia obiektu w obiekcie. <xref:System.Data.Services.Client.MergeOption.NoTracking> Wartość tożsamości jest również używana do zagwarantowania, że jest tworzone tylko pojedyncze wystąpienie jednostki, nawet jeśli jednostka jest zwracana wiele razy w odpowiedzi na zapytanie.

3. Biblioteka kliencka odczytuje właściwości z wpisu kanału informacyjnego i ustawia odpowiednie właściwości dla nowo utworzonego obiektu. Gdy obiekt mający taką samą wartość tożsamości występuje już w <xref:System.Data.Services.Client.DataServiceContext>, właściwości są ustawiane na podstawie <xref:System.Data.Services.Client.MergeOption> ustawienia <xref:System.Data.Services.Client.DataServiceContext>. Odpowiedź może zawierać wartości właściwości, dla których odpowiednia właściwość nie występuje w typie klienta. W takim przypadku akcja zależy od wartości <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> właściwości. <xref:System.Data.Services.Client.DataServiceContext> Gdy ta właściwość jest ustawiona na `true`, Brakująca właściwość jest ignorowana. W przeciwnym razie zostanie zgłoszony błąd. Właściwości są ustawiane w następujący sposób:

    - Właściwości skalarne są ustawiane na odpowiadającą jej wartość we wpisie w komunikacie odpowiedzi.

    - Właściwości złożone są ustawiane na nowe wystąpienie typu złożonego, które są ustawiane przy użyciu właściwości typu złożonego z odpowiedzi.

    - Właściwości nawigacji, które zwracają kolekcję powiązanych jednostek <xref:System.Collections.Generic.ICollection%601>, są ustawiane na nowe lub istniejące wystąpienie, gdzie `T` jest typem powiązanej jednostki. Ta kolekcja jest pusta, chyba że powiązane obiekty zostały załadowane do <xref:System.Data.Services.Client.DataServiceContext>. Aby uzyskać więcej informacji, zobacz [ładowanie odroczonej zawartości](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).

      > [!NOTE]
      > Gdy wygenerowane klasy danych klienta obsługują powiązanie danych, w zamian zwraca wystąpienia <xref:System.Data.Services.Client.DataServiceCollection%601> klasy. Aby uzyskać więcej informacji, zobacz [Powiązywanie danych z kontrolkami](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).

4. <xref:System.Data.Services.Client.DataServiceContext.ReadingEntity> Zdarzenie jest zgłaszane.

5. Biblioteka klienta dołącza obiekt do <xref:System.Data.Services.Client.DataServiceContext>. Obiekt nie jest dołączany, <xref:System.Data.Services.Client.MergeOption> gdy <xref:System.Data.Services.Client.MergeOption.NoTracking>jest.

## <a name="see-also"></a>Zobacz także

- [Wykonywanie zapytań do usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
- [Projekcje zapytania](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)
