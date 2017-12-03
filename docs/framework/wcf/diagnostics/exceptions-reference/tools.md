---
title: "Narzędzia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89c907f9-313f-408c-992a-631f1eadf1da
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 174459c23bd6ecd336394146b6d91e265cb820d3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="tools"></a>Narzędzia
W tym temacie wymieniono wszystkie wyjątki generowane przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] narzędzia.  
  
## <a name="exception-list"></a>Listy wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|ParametersTarget|\<wyliczenia >|  
|ParametersToolConfig|\<configFile >|  
|ErrInvalidPath|Określony jest nieprawidłową ścieżkę. Sprawdź właściwość określonego argumentu.|  
|ParametersReference|\<Ścieżka pliku >|  
|WrnCannotLoadConfigFileForValidation|Wystąpił błąd podczas przetwarzania pliku konfiguracji z określonej lokalizacji. Nie można sprawdzić poprawności usług, które są zdefiniowane w tym pliku konfiguracji.|  
|MoreHelp|Aby uzyskać pomoc wpisz "svcutil" z określonymi argumentami.|  
|HelpMergeConfig|Powoduje, że wygenerowany konfiguracji do scalenia do istniejącego pliku zamiast zastępowanie istniejącego pliku.|  
|ErrCannotWriteFile|Nie można zapisać do pliku wyjściowego.|  
|ErrInvalidNamespaceArgument|Określona wartość nieprawidłowa został przekazany do określonej opcji. Określ rozdzielaną przecinkami docelowej przestrzeni nazw i para przestrzeni nazw CLR.|  
|HelpImportXmlType|Konfiguruje serializator DataContract do importowania typów innych niż typ jako typów IXmlSerializable.|  
|ErrExclusiveOptionsSpecified|Nie można użyć określonej opcji, gdy określono określona opcja.|  
|WrnHttpGetFailed|Błąd pobrania HTTP z określonym identyfikatorem URI.|  
|ErrInputFileNotAssemblyOrMetadata|Nie ma pliku w określonej lokalizacji odczytać za pomocą określonego argumentu wejściowego pliku XML metadanych lub prawidłowy zestaw.|  
|WrnUnknownMetadataFound|Nie można zapisać dokumentu Nierozpoznane metadane określonego typu.|  
|ErrDirectoryContainsInvalidCharacters|Określona wartość nieprawidłowa został przekazany do określonej opcji. Określony znak jest niedozwolone w ścieżce.|  
|WrnCannotResolveServiceForValidation|Nie można załadować usługi za pomocą określonego configName. Aby sprawdzić poprawność usługi, podaj zarówno zestaw zawierający typ usługi, jak i plik wykonywalny z konfiguracją dla tej usługi.|  
|ErrUnexpectedValue|Określona opcja nie obsługuje żadnych wartości.|  
|#InvalidArg|Określony zawiera nieprawidłowy argument.|  
|ParametersExcludeType|\<Typ >|  
|HelpXmlSerializer|Generowanie typów danych, które używają XmlSerializer do serializacji i deserializacji.|  
|#|---------------------------------------------------------------------------------------------------------------------=|  
|ErrUnexpectedError|Wystąpił błąd w narzędziu.|  
|HelpNologo|Komunikat o prawach autorskich oraz transparent zostało pominięte.|  
|ErrInputConflictsWithTarget|Typ wejściowy odczytu z określonego nie jest obsługiwana z opcją określonego równa określonej wartości.|  
|WrnCannotLoadServiceForExport|Wystąpił błąd podczas ładowania typu usługi do wyeksportowania.|  
|HelpMetadataDownloadCategory|-= POBIERANIE METADANYCH =-|  
|WrnNoServiceContractTypes|Nie można wygenerować typy XmlSerializer dla określonego zestawu. Nie znaleziono żadnych typów kontraktu usługi.|  
|WrnCouldNotLoadTypesFromReferenceAssemblyAt|Wystąpił błąd podczas ładowania typów w zestawie, do którego został załadowany z określonego. Niektóre typy w zestawie nie może zostać załadowany i nie są dostępne do narzędzia.|  
|ErrDirectoryPointsToAFile|Określona wartość nieprawidłowa został przekazany do określonej opcji. Określona wartość jest ścieżka do pliku.|  
|Błąd|Błąd:|  
|ErrDuplicateReferenceValues|Określony zestaw został załadowany, dwukrotnie przy użyciu określonej opcji. Zestawu może być tylko odwołanie jednokrotnie.|  
|WrnNoXmlSerializerOperationBehavior|Nie można wygenerować XmlSerializer dla określonego zestawu. Nie kontraktu usługi w zestawie ma operację, podając XmlSerializerOperationBehavior.|  
|ErrCannotCreateDirectory|Nie można utworzyć określonego katalogu.|  
|ErrCouldNotLoadTypesFromAssemblyAt|Nie można załadować żadnych typów w określonym zestawie.|  
|ErrUnknownSwitch|Określony przełącznik jest nierozpoznaną opcję.|  
|logo|Logo narzędzia jest "Microsoft® narzędzia modelu usług metadanych" z wersją.|  
|NoCodeWasGenerated|Nie wygenerowano kodu.<br /><br /> Jeśli chcesz wygenerować klient, może to być spowodowane dokumentów metadanych nie zawiera żadnych prawidłowych umów lub usług<br /><br /> lub ponieważ wszystkie kontrakty/usługi zostały odnalezione w zestawy referencyjne występują. Sprawdź wszystkich dokumentów metadanych został przekazany do narzędzia.|  
|WrnUnableToLoadContractForSGen|Wystąpił błąd podczas ładowania typu kontraktu. Nie można wygenerować typu XmlSerializer dla tego kontraktu. Określony typ i szczegóły.|  
|WrnOptionConflictsWithInput|Nie można użyć określonej opcji z wielu zestawów wejściowych. Określona opcja została zignorowana.|  
|ErrUnableToImportMetadata|Wystąpił błąd krytyczny podczas próby zaimportowania metadanych.|  
|ErrInvalidSerializer|Określona opcja przekazano wartość serializator jest nieprawidłowy. Określono obsługiwanych serializatorów.|  
|SavingDownloadedMetadata|Zapisywanie metadanych pobranych plików...|  
|WrnNoConfigForServices|Żaden zestawów przekazany nie był pliki wykonywalne z pliku konfiguracji lub Brak konfiguracji usług plików znajdujących się o nazwie określonej konfiguracji.|  
|ErrInputConflictsWithOption|Nie można użyć danych wejściowych z określonego do odczytu z opcją określony, ponieważ ich pociąga za sobą różne tryby pracy narzędzia.|  
|ErrUnableToExportEndpoints|Wystąpił błąd podczas eksportowania określonego typu.|  
|ErrInputSchemaParseError|Wystąpił błąd analizy schemat XML podczas odczytywania określonego. Sprawdź, czy plik XML jest poprawnie sformułowany i prawidłowe.|  
|ErrInputPolicyParseError|Podczas odczytywania określonego wystąpił błąd podczas analizowania WS-Policy. Sprawdź, czy plik XML jest poprawnie sformułowany i prawidłowe.|  
|ErrUnableToLoadReferenceType|Wystąpił błąd podczas ładowania typu kontraktu do którego istnieje odwołanie. Ten typ określony jest ignorowana.|  
|WrnCannotLoadServiceForValidation|Wystąpił błąd podczas ładowania usługi do sprawdzenia poprawności. Określony typ i szczegóły.|  
|HelpCodeGenerationCategory|-= GENEROWANIE KODU =-|  
|RetreivingMetadataWithMexAndDisco|Próba pobrania metadanych z określonego za pomocą usługi WS-Metadata Exchange lub DISCO.|  
|ErrGeneralSchemaValidation|Wystąpił błąd podczas weryfikacji schematów XML, które zostały wygenerowane podczas eksportowania.|  
|ParametersDirectory|\<katalogu >|  
|ErrCannotLoadSpecifiedType|Typ nie może być załadowany dla określonej wartości, który został przekazany do określonej opcji. Upewnij się, że tego typu należy do zestawu został określony przy użyciu określonej opcji.|  
|ErrOptionModeConflict|Określona opcja nie można używać z określona opcja, ponieważ ich oznacza dane wyjściowe różnych typów.|  
|ErrIsNotAnAssembly|Nie można załadować określonego zestawu. Sprawdź, czy ten plik jest zestawem .NET.|  
|ErrInputConflictsWithMode|Dane wejściowe z określonego do odczytu jest niespójny z innymi opcjami.|  
|ErrDuplicateValuePassedToTypeArg|Określona wartość został przekazany do określoną opcję wiele razy. Każdy typ można określić tylko raz.|  
|ErrInputEPRFileParseError|Nie można odczytać odwołania do punktu końcowego z określonego. Sprawdź, czy plik XML jest poprawnie sformułowany i prawidłowe.|  
|ErrCouldNotCreateCodeProvider|Nie można utworzyć dostawcy kodu dla określonej wartości, który został przekazany do argumentu /{1}. Sprawdź dostawcę kodu jest poprawnie zainstalowana i skonfigurowana.|  
|ErrPathTooLongDirOnly|Wynikowe określona ścieżka jest za długa. Przejrzyj określonego argumentu.|  
|HelpDataContractSerializer|Generowanie typów danych, które używają serializator DataContract do serializacji i deserializacji.|  
|ErrUnableToExportEndpoint|Wystąpił błąd podczas eksportowania Nazwa punktu końcowego określona w określonej przestrzeni nazw w znaleziono w pliku konfiguracyjnym załadowany dla zestawu typu określonej usługi.|  
|HelpUsage1|Wyświetla Pomoc użycia.|  
|HelpUsage2|Wyświetla Pomoc użycia.|  
|HelpUsage3|Wyświetla Pomoc użycia.|  
|HelpUsage4|Wyświetla Pomoc użycia.|  
|HelpUsage5|Wyświetla Pomoc użycia.|  
|ErrDirectoryNotFound|Nie można odnaleźć określonego katalogu. Sprawdź, czy katalog istnieje i czy masz odpowiednie uprawnienia do jego odczytu.|  
|ErrUnableToLoadFile|Nie można odczytać określonego pliku.|  
|ErrNoFilesFound|Określona ścieżka wejściowa nie można znaleźć wszystkie istniejące pliki.|  
|ParametersConfig|\<configFile >|  
|ErrDirectoryInsteadOfFile|Określona ścieżka wejściowa wydaje się być katalogiem. Dane wejściowe muszą być adresy URL lub ścieżki pliku.|  
|HelpConfig|Powoduje, że narzędzia do generowania pliku konfiguracji o podanej nazwie. Domyślne: output.config.|  
|ErrSingleUseSwitch|Nie można określić opcji określony wiele razy.|  
|Ostrzeżenie|Ostrzeżenie:|  
|WrnAmbiguousServiceConfig|Odnaleziono wiele konfiguracji usługi o nazwie określonej konfiguracji, są określone następujące zestawy.|  
|ErrInvalidInputPath|Określona ścieżka wejściowa nie można znaleźć wszystkie istniejące pliki i prawdopodobnie nie jest prawidłowym identyfikatorem URI.|  
|ErrUnableToLoadInputs|Wystąpił błąd podczas odczytywania metadanych załadowany.|  
|GeneratingSerializer|Trwa generowanie serializatorów XML...|  
|HelpToolConfig|Plik konfiguracji niestandardowej do użycia zamiast pliku konfiguracji aplikacji. To umożliwia zmianę konfiguracji metadanych lub zarejestrować bez modyfikacji pliku konfiguracji narzędzia konfiguracji rozszerzenia.|  
|ErrValidateInvalidUse|Określona opcja nie można używać z określoną opcję.|  
|WrnWSMExFailed|Błąd WS-Metadata Exchange określonego identyfikatora URI.|  
|HelpNoconfig|Nie generują konfiguracji.|  
|HelpCodeGenerationDescription|Określony może spowodować wygenerowanie usługi kontrakty, klientów i typy danych dokumentów metadanych.|  
|HelpTargetMetadata|Metadane w danych wyjściowych. Jeśli dane wejściowe jest adres URL, Svcutil.exe metadanych jest zapisywany na dysku i nie powoduje generowania kodu. Jeśli dane wejściowe jest jeden lub więcej zestawów, Svcutil.exe generuje metadanych z typów w zestawach.|  
|ErrAmbiguousOptionModeConflict|Określona opcja koliduje z innymi opcjami. Przeglądanie tego użycia narzędzia.|  
|ErrNotLanguageOrCodeDomType|Określona wartość, który został przekazany do określonego argumentu nie odpowiada zdefiniowanych języka i nie można załadować jako typu CLR w pełni kwalifikowana.|  
|ErrUnableToUniquifyFilename|Nie można utworzyć pliku wyjściowego. Zbyt wiele plików tworzonych z określonym prefiksem.|  
|ErrCannotCreateFile|Nie można utworzyć określony plik wyjściowy.|  
|ErrExpectedValue|Określona opcja wymaga określenia wartości.|  
|ErrCannotDisambiguateSpecifiedTypes|Więcej niż jeden typ o takiej samej nazwie istnieje w zestawie zestawów występujących w odwołaniach. Umożliwia rozróżnianie między określonych typów określona opcja kwalifikowana nazwa zestawu.|  
|RetreivingMetadataWithMexOnly|Próba pobrania metadanych z określonej lokalizacji za pomocą usługi WS-Metadata Exchange. Ten adres URL nie obsługuje DISCO.|  
|ErrInvalidTarget|Określony element docelowy jest nieprawidłowy, gdy określona za pomocą określonej opcji. Obsługiwane elementy docelowe zostały określone.|  
|ErrPathTooLong|Wynikowe ścieżka jest za długa. Przejrzyj określonych argumentów.|  
|HelpCommonOptionsCategory|-= TYPOWE OPCJE =-|  
|ParametersServiceName|\<serviceConfigName >|  
|ErrNoValidInputFilesSpecified|Nie prawidłowy określono plików wejściowych. Określ dokumentów metadanych lub zestawu plików.|  
|ParametersLanguage|\<język >|  
|ErrUnableToLoadMetadataDocument|Wystąpił błąd podczas odczytywania metadanych z jednego z załadować dokumentów. Identyfikator dokumentu jest określona.|  
|ErrConflictingInputs|Określony argument wejściowy jest w konflikcie z określony, ponieważ ich pociąga za sobą różne tryby pracy narzędzia.|  
|WrnUnableToLoadContractForValidation|Wystąpił błąd podczas ładowania typu kontraktu. Określony typ i szczegóły.|  
|WrnAttributeReflectionErrors|Atrybut odbicia nie powiodło się dla niektórych typów w zestawie, które zostały załadowane z określonego. Sprawdź, czy ten można załadować zestawu z tej lokalizacji z uprawnieniami prawa zabezpieczeń.|  
|HelpMetadataExportCategory|-= EKSPORTOWANIE METADANYCH =-|  
|HelpValidationCategory|-= WERYFIKACJA USŁUG =-|  
|ValidationError|Błąd sprawdzania poprawności:|  
|GeneratingFiles|Generowanie plików...|  
|ErrCannotSpecifyMultipleMappingsForNamespace|Nieprawidłowa wartość została przekazana do określonej opcji. Określony docelowy obszar nazw nie można zamapować na wiele nazw CLR określone.|  
|ErrCouldNotLoadReferenceAssemblyAt|Nie można załadować zestawu określonego odwołania.|  
|ParametersOut|\<Plik >|  
|NoCodeWasGeneratedSuggestDCOnly|Aby wygenerować kontraktów na podstawie schematów, opcja określony.|  
|ErrUnableToLoadInputConfig|Nie można załadować określonego pliku konfiguracji.|  
|ErrUnexpectedDelimiter|Nieprawidłowy argument ogranicznikiem (":" lub "=") nie można uruchomić opcji.|  
|ErrMergeConfigUsedWithoutConfig|Nie można użyć opcji określony bez określenia określoną opcję.|  
|ErrUnableToExportContract|Wystąpił błąd podczas eksportowania umowy z określonego typu.|  
|GeneratingMetadata|Generowanie plików metadanych...|  
|ErrNotCodeDomType|Określony typ, który został przekazany do określony argument nie jest określony klasy pochodnej.|  
|WrnNoTypeForServices|Brak zestawów, które zostały przekazane typów zawartych w niej usługi o nazwie określonej konfiguracji.|  
|ErrAssemblyLoadFailed|Nie można załadować określonego pliku zestawu. Aby uzyskać więcej informacji, sprawdź FusionLogs.|  
|NoMetadataWasGenerated|Nie wygenerowano żadnych plików metadanych. Żaden kontrakt usługi zostały wyeksportowane.<br /><br /> Aby wyeksportować usługi, należy użyć określonej opcji. Aby wyeksportować kontraktów danych, należy określić opcję.|  
|WrnCannotResolveServiceForExport|Nie można załadować usługi za pomocą określonego configName. Aby wyeksportować usługi, należy podać zestaw zawierający typ usługi, jak i plik wykonywalny z konfiguracją dla tej usługi.|  
|ParametersCollectionType|\<Typ >|  
|ErrOptionConflictsWithTarget|Użyj określonej opcji nie jest obsługiwana z opcją określonego równa określonej wartości.|  
|ErrCodegenError|Wystąpił błąd podczas generowania kodu w określonym języku.<br /><br /> Język nie obsługuje wszystkie elementy kodu generowany. Należy użyć innego języka.|  
|ErrInputWsdlParseError|Podczas odczytywania określonego wystąpił podczas WSDL błąd analizy. Sprawdź, czy plik XML jest poprawnie sformułowany i prawidłowe.|  
|ErrCouldNotCreateInstance|Nie można utworzyć wystąpienia określonego typu, który został przekazany do określonego argumentu.|  
|ParametersNamespace|\<ciąg, ciąg >|  
|HelpNostdlib|Nie odwołuj się do bibliotek standardowych (domyślnie mscorlib.dll i system.servicemodel.dll odwołują.)|  
|WrnCannotLoadConfigFileForExport|Wystąpił błąd podczas przetwarzania pliku konfiguracji, który został załadowany z określonego. Nie można załadować usługi, które są zdefiniowane w tym pliku konfiguracji.|  
|WrnUnableToLoadContractForExport|Wystąpił błąd podczas ładowania typu kontraktu. Nie można wyeksportować tego określonego typu.|
