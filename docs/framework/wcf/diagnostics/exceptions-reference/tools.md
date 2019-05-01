---
title: Narzędzia
ms.date: 03/30/2017
ms.assetid: 89c907f9-313f-408c-992a-631f1eadf1da
ms.openlocfilehash: 6c4ada74c2fc6aba84eb1fe46f4d7cdee9978d13
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780747"
---
# <a name="tools"></a>Narzędzia
Ten temat zawiera listę wszystkich wyjątków generowanych przez narzędzia Windows Communication Foundation (WCF).  
  
## <a name="exception-list"></a>Lista wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|ParametersTarget|\<enum>|  
|ParametersToolConfig|\<configFile>|  
|ErrInvalidPath|Określony jest nieprawidłową ścieżką. Sprawdź określony argument.|  
|ParametersReference|\<Ścieżka pliku >|  
|WrnCannotLoadConfigFileForValidation|Wystąpił błąd podczas przetwarzania pliku konfiguracji z określonej lokalizacji. Nie można zweryfikować usług, które są zdefiniowane w tym pliku konfiguracji.|  
|MoreHelp|Aby uzyskać dodatkową pomoc wpisz "svcutil /" z określonymi argumentami.|  
|HelpMergeConfig|Powoduje, że wygenerowaną konfigurację do scalenia do istniejącego pliku zamiast nadpisywać istniejący plik.|  
|ErrCannotWriteFile|Nie można zapisać do pliku wyjściowego.|  
|ErrInvalidNamespaceArgument|Określona nieprawidłowa wartość został przekazany do określoną opcję. Określ rozdzielaną przecinkami docelowego obszaru nazw i pary nazw środowiska CLR.|  
|HelpImportXmlType|Konfiguruje serializator DataContract do importowania typów innych niż typ jako typów IXmlSerializable.|  
|ErrExclusiveOptionsSpecified|Nie można użyć określonej opcji, gdy określono określoną opcję.|  
|WrnHttpGetFailed|Błąd Pobierz HTTP przy użyciu określonego identyfikatora URI.|  
|ErrInputFileNotAssemblyOrMetadata|Nie ma pliku w określonej lokalizacji odczytać za pomocą określonego argumentu wejściowego pliku XML metadanych lub prawidłowy zestaw.|  
|WrnUnknownMetadataFound|Nie można zapisać dokumentu Nierozpoznane metadane określonego typu.|  
|ErrDirectoryContainsInvalidCharacters|Określona nieprawidłowa wartość został przekazany do określoną opcję. Określony znak jest niedozwolona w ścieżce.|  
|WrnCannotResolveServiceForValidation|Nie można załadować usługi za pomocą określonego configName. Aby sprawdzić działanie usługi, należy podać zarówno zestaw, który zawiera typ usługi, jak i plik wykonywalny z konfiguracją dla tej usługi.|  
|ErrUnexpectedValue|Określona opcja nie obsługuje żadnych wartości.|  
|#InvalidArg|Określony zawiera nieprawidłowy argument.|  
|ParametersExcludeType|\<type>|  
|HelpXmlSerializer|Generuj typy danych używające serializatora XmlSerializer w ramach serializacji i deserializacji.|  
|#|---------------------------------------------------------------------------------------------------------------------=|  
|ErrUnexpectedError|Wystąpił błąd w narzędziu.|  
|HelpNologo|Nie jest wyświetlany komunikat o prawach autorskich i baneru.|  
|ErrInputConflictsWithTarget|Odczyt wejścia z określonego typu nie jest obsługiwany z określoną opcję równa określonej wartości.|  
|WrnCannotLoadServiceForExport|Wystąpił błąd podczas ładowania typ usługi do wyeksportowania.|  
|HelpMetadataDownloadCategory|-= POBIERANIE METADANYCH =-|  
|WrnNoServiceContractTypes|Nie można wygenerować typy elementu XmlSerializer dla określonego zestawu. Nie znaleziono żadnych typów kontraktu usługi.|  
|WrnCouldNotLoadTypesFromReferenceAssemblyAt|Wystąpił błąd podczas ładowania typów w zestawie, który został załadowany z określonego. Niektóre typy w zestawie nie może zostać załadowany i nie są dostępne do narzędzia.|  
|ErrDirectoryPointsToAFile|Określona nieprawidłowa wartość został przekazany do określoną opcję. Określona wartość jest ścieżka do pliku.|  
|Błąd|Błąd:|  
|ErrDuplicateReferenceValues|Określony zestaw został załadowany, dwa razy, używając określoną opcję. Zestawu może być tylko odwołania jeden raz.|  
|WrnNoXmlSerializerOperationBehavior|Nie można wygenerować elementu XmlSerializer dla określonego zestawu. Nie kontraktu usługi w zestawie ma operację, używając XmlSerializerOperationBehavior.|  
|ErrCannotCreateDirectory|Nie można utworzyć określonego katalogu.|  
|ErrCouldNotLoadTypesFromAssemblyAt|Nie można załadować żadnych typów w określonym zestawie.|  
|ErrUnknownSwitch|Określony przełącznik jest nierozpoznaną opcję.|  
|Logo|Logo narzędzia jest "Narzędzia firmy Microsoft® Service Model metadanych" wersją.|  
|NoCodeWasGenerated|Wygenerowano żadnego kodu.<br /><br /> Jeśli próbowano wygenerować klienta, może to być spowodowane przez dokumenty metadanych nie zawiera żadnych prawidłowych kontraktów lub usług<br /><br /> lub, ponieważ wszystkie kontrakty/usługi zostały odnalezione jako istniejące w zestawach referencyjnych. Sprawdź przekazano wszystkie dokumenty metadanych do narzędzia.|  
|WrnUnableToLoadContractForSGen|Wystąpił błąd podczas ładowania typu kontraktu. Nie można wygenerować typu elementu XmlSerializer dla tego kontraktu. Określony typ i szczegółowe informacje.|  
|WrnOptionConflictsWithInput|Nie można używać określoną opcję z wielu zestawów danych wejściowych. Określona opcja jest ignorowana.|  
|ErrUnableToImportMetadata|Wystąpił błąd krytyczny podczas próby zaimportowania metadanych.|  
|ErrInvalidSerializer|Nieprawidłowa wartość serializatora został przekazany do określoną opcję. Obsługiwane serializatory są określone.|  
|SavingDownloadedMetadata|Zapisywanie metadanych pobranych plików...|  
|WrnNoConfigForServices|Brak zestawów przekazywane były pliki wykonywalne z pliku konfiguracji lub brak usług pliki znajdujące się w konfiguracji o nazwie określonej konfiguracji.|  
|ErrInputConflictsWithOption|Dane wejściowe odczytane z określonego nie można używać z określoną opcję, ponieważ oznaczają inne tryby działania narzędzia.|  
|ErrUnableToExportEndpoints|Wystąpił błąd podczas eksportowania określonego typu.|  
|ErrInputSchemaParseError|Wystąpił błąd analizy schematu XML podczas odczytu określonego. Sprawdź, czy kod XML jest dobrze sformułowany i prawidłowy.|  
|ErrInputPolicyParseError|Wystąpił błąd analizy zasad WS podczas odczytu określonego. Sprawdź, czy kod XML jest dobrze sformułowany i prawidłowy.|  
|ErrUnableToLoadReferenceType|Wystąpił błąd podczas ładowania typu odwołania kontraktu. Ten określony typ jest ignorowane.|  
|WrnCannotLoadServiceForValidation|Wystąpił błąd podczas ładowania usługi, który ma zostać zweryfikowana. Określony typ i szczegółowe informacje.|  
|HelpCodeGenerationCategory|-= GENEROWANIE KODU =-|  
|RetreivingMetadataWithMexAndDisco|Próba pobrania metadanych z określonego za pomocą usługi WS-Metadata Exchange lub NAJDYWANIA.|  
|ErrGeneralSchemaValidation|Wystąpił błąd podczas weryfikacji schematów XML, które zostały wygenerowane podczas eksportowania.|  
|ParametersDirectory|\<directory>|  
|ErrCannotLoadSpecifiedType|Brak typu mogą zostać załadowane dla określonej wartości, który został przekazany do określoną opcję. Upewnij się, czy zestawu, do której należy ten typ jest określony, przy użyciu określonej opcji.|  
|ErrOptionModeConflict|Nie można używać określoną opcję z określoną opcję, ponieważ oznaczają inne typy wyjściowe.|  
|ErrIsNotAnAssembly|Nie można załadować określonego zestawu. Sprawdź, czy ten plik jest zestawem .NET.|  
|ErrInputConflictsWithMode|Dane wejściowe odczytane z określonego jest niespójny z innymi opcjami.|  
|ErrDuplicateValuePassedToTypeArg|Określona wartość została przekazana do opcji/określony wiele razy. Każdy typ można określić tylko raz.|  
|ErrInputEPRFileParseError|Nie można odczytać odwołania do punktu końcowego z określonego. Sprawdź, czy kod XML jest dobrze sformułowany i prawidłowy.|  
|ErrCouldNotCreateCodeProvider|Nie można utworzyć dostawcy kodu dla określonej wartości, która została przekazana /{1} argumentu. Sprawdź, czy zainstalowano i skonfigurowano dostawcy kodu.|  
|ErrPathTooLongDirOnly|Wynikowe określona ścieżka jest za długa. Przejrzyj określony argument.|  
|HelpDataContractSerializer|Generuj typy danych używające serializatora DataContract do serializacji i deserializacji.|  
|ErrUnableToExportEndpoint|Wystąpił błąd podczas eksportowania z nazwą wskazany punkt końcowy w określonej przestrzeni nazw w określonym typie znalezione w pliku konfiguracyjnym ładowane do zestawu.|  
|HelpUsage1|Wyświetla Pomoc użycia.|  
|HelpUsage2|Wyświetla Pomoc użycia.|  
|HelpUsage3|Wyświetla Pomoc użycia.|  
|HelpUsage4|Wyświetla Pomoc użycia.|  
|HelpUsage5|Wyświetla Pomoc użycia.|  
|ErrDirectoryNotFound|Nie można odnaleźć określonego katalogu. Sprawdź, czy katalog istnieje i czy masz odpowiednie uprawnienia do jego odczytu.|  
|ErrUnableToLoadFile|Nie można odczytać określonego pliku.|  
|ErrNoFilesFound|Określona ścieżka wejściowa nie wydaje się odwoływać do żadnych istniejących plików.|  
|ParametersConfig|\<configFile>|  
|ErrDirectoryInsteadOfFile|Określona ścieżka wejściowa wydaje się być katalogiem. Dane wejściowe muszą być adresami URL lub ścieżkami do plików.|  
|HelpConfig|Powoduje, że narzędzia, aby wygenerować plik konfiguracji o podanej nazwie. Domyślne: output.config.|  
|ErrSingleUseSwitch|Nie można określić opcji określony wiele razy.|  
|Ostrzeżenie|Ostrzeżenie:|  
|WrnAmbiguousServiceConfig|Znaleziono wiele konfiguracji usługi o nazwie określonej konfiguracji następujące zestawy są określone.|  
|ErrInvalidInputPath|Określona ścieżka wejściowa nie wydaje się odwoływać do żadnych istniejących plików i prawdopodobnie nie jest prawidłowym identyfikatorem URI.|  
|ErrUnableToLoadInputs|Wystąpił błąd podczas odczytu załadowanych metadanych.|  
|GeneratingSerializer|Trwa generowanie serializatory XML...|  
|HelpToolConfig|Plik konfiguracji niestandardowej, należy użyć zamiast pliku konfiguracji aplikacji. To można zmienić konfigurację metadanych lub zarejestruj rozszerzenia konfiguracji bez zmiany pliku konfiguracji tego narzędzia.|  
|ErrValidateInvalidUse|Nie można używać określoną opcję z określoną opcję.|  
|WrnWSMExFailed|Wystąpił błąd podczas wymiany protokołu WS-Metadata przy użyciu określonego identyfikatora URI.|  
|HelpNoconfig|Nie generują konfiguracji.|  
|HelpCodeGenerationDescription|Określony może generować usługi kontrakty, klientów i typy danych z dokumentów metadanych.|  
|HelpTargetMetadata|Metadane wyjściowe. Jeśli dane wejściowe jest adres URL, Svcutil.exe zapisuje metadane na dysku i nie generuje kodu. Jeśli dane wejściowe są jeden lub więcej zestawów, Svcutil.exe generuje metadanych z typów w zestawach.|  
|ErrAmbiguousOptionModeConflict|Określona opcja konflikty z innymi opcjami. Sprawdź sposób korzystania z narzędzia.|  
|ErrNotLanguageOrCodeDomType|Określona wartość, która została przekazana do określonego argumentu nie reprezentuje zdefiniowanego języka i nie można załadować jako w pełni kwalifikowanego typu CLR.|  
|ErrUnableToUniquifyFilename|Nie można utworzyć nazwy pliku wyjściowego. Zbyt wiele plików jest tworzonych za pomocą określonego prefiksu.|  
|ErrCannotCreateFile|Nie można utworzyć pliku określonym produktem wyjściowym.|  
|ErrExpectedValue|Określona opcja wymaga, należy określić wartość.|  
|ErrCannotDisambiguateSpecifiedTypes|Istnieje więcej niż jeden typ o takiej samej nazwie w zbiorze przywoływanych zestawów. Użyj nazw kwalifikowanych dla zestawu rozróżnienie między określonych typów określonej opcji.|  
|RetreivingMetadataWithMexOnly|Próba pobrania metadanych z określonej lokalizacji za pomocą usługi WS-Metadata Exchange. Ten adres URL nie obsługuje NAJDYWANIA.|  
|ErrInvalidTarget|Określony obiekt docelowy jest nieprawidłowy, gdy określona za pomocą określoną opcję. Obsługiwane obiekty docelowe są określone.|  
|ErrPathTooLong|Ścieżka wynikowa jest za długa. Przejrzyj określonych argumentów.|  
|HelpCommonOptionsCategory|-= TYPOWE OPCJE =-|  
|ParametersServiceName|\<serviceConfigName>|  
|ErrNoValidInputFilesSpecified|Nie określono prawidłowych plików wejściowych. Określ dokumentów metadanych lub zestawu plików.|  
|ParametersLanguage|\<język >|  
|ErrUnableToLoadMetadataDocument|Wystąpił błąd podczas odczytywania metadanych z jednego z załadowanych dokumentów. Określono identyfikator dokumentu.|  
|ErrConflictingInputs|Określony argument wejściowy wystąpił konflikt między określony, ponieważ oznaczają inne tryby działania narzędzia.|  
|WrnUnableToLoadContractForValidation|Wystąpił błąd podczas ładowania typu kontraktu. Określony typ i szczegółowe informacje.|  
|WrnAttributeReflectionErrors|Atrybut odbicia nie powiodła się dla niektórych typów w zestawie, które zostały załadowane z określonego. Sprawdź, czy tego zestawu można załadować z tej lokalizacji z uprawnieniami zabezpieczeń prawo.|  
|HelpMetadataExportCategory|-= EKSPORTOWANIE METADANYCH =-|  
|HelpValidationCategory|-= WALIDACJA USŁUG =-|  
|ValidationError|Błąd sprawdzania poprawności:|  
|GeneratingFiles|Trwa generowanie plików...|  
|ErrCannotSpecifyMultipleMappingsForNamespace|Nieprawidłowa wartość został przekazany do określoną opcję. Nie można zamapować określonego docelowego obszaru nazw na wiele przestrzeni nazw CLR, jak określono.|  
|ErrCouldNotLoadReferenceAssemblyAt|Nie można załadować zestawu określone odwołanie.|  
|ParametersOut|\<file>|  
|NoCodeWasGeneratedSuggestDCOnly|Aby generować kontrakty od schematów, użyj określoną opcję.|  
|ErrUnableToLoadInputConfig|Nie można załadować określonego pliku konfiguracji.|  
|ErrUnexpectedDelimiter|Nieprawidłowy argument ogranicznika (":" lub "=") nie można uruchomić opcji.|  
|ErrMergeConfigUsedWithoutConfig|Nie można użyć opcji określony bez określenia określoną opcję.|  
|ErrUnableToExportContract|Wystąpił błąd podczas eksportowania kontrakt załadowanych z określonego typu.|  
|GeneratingMetadata|Trwa generowanie plików metadanych...|  
|ErrNotCodeDomType|Określony typ, który został przekazany do określony argument nie jest określony klasy pochodnej.|  
|WrnNoTypeForServices|Brak zestawów, które zostały przekazane typy zawarte usługi o nazwie określonej konfiguracji.|  
|ErrAssemblyLoadFailed|Nie można załadować określonego pliku zestawu. Aby uzyskać więcej informacji, sprawdź FusionLogs.|  
|NoMetadataWasGenerated|Nie wygenerowano żadnych plików metadanych. Wyeksportowano nie kontraktów usług.<br /><br /> Aby wyeksportować usługi, należy użyć określoną opcję. Aby wyeksportować kontraktów danych, określ opcję.|  
|WrnCannotResolveServiceForExport|Nie można załadować usługi za pomocą określonego configName. Aby wyeksportować usługi, należy podać zestaw, który zawiera typ usługi, jak i plik wykonywalny z konfiguracją dla tej usługi.|  
|ParametersCollectionType|\<type>|  
|ErrOptionConflictsWithTarget|Korzystanie z określonej opcji nie jest obsługiwana z określoną opcję równa określonej wartości.|  
|ErrCodegenError|Wystąpił błąd podczas generowania kodu w wybranym języku.<br /><br /> Język nie obsługuje wszystkie elementy kodu są generowane. Powinien być używany inny język.|  
|ErrInputWsdlParseError|Wystąpił błąd analizy WSDL podczas odczytu określonego. Sprawdź, czy kod XML jest dobrze sformułowany i prawidłowy.|  
|ErrCouldNotCreateInstance|Nie można utworzyć wystąpienia określonego typu, który został przekazany do określonego argumentu.|  
|ParametersNamespace|\<ciąg, ciąg >|  
|HelpNostdlib|Nie odwołuj się do standardowych bibliotek (domyślnie mscorlib.dll i system.servicemodel.dll są przywoływane.)|  
|WrnCannotLoadConfigFileForExport|Wystąpił błąd podczas przetwarzania pliku konfiguracji, który został załadowany z określonego. Nie można załadować usług, które są zdefiniowane w tym pliku konfiguracji.|  
|WrnUnableToLoadContractForExport|Wystąpił błąd podczas ładowania typu kontraktu. Nie można wyeksportować tego określonego typu.|
