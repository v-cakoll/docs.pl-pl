### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>ObjectContext.Translate i ObjectContext.ExecuteStoreQuery obsługują teraz typu wyliczeniowego

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.0, parametr ogólny <code>T</code> z <code>ObjectContext.Translate</code> i <code>ObjectContext.ExecuteStoreQuery</code> metody może nie być wyliczeniem. Ten scenariusz jest teraz obsługiwane.|
|Sugestia|Jeśli Translate lub ExecuteStoreQuery została wywołana dla typu wyliczeniowego w .NET Framework 4.0, "0" została zwrócona. Jeśli to zachowanie pożądane, wywołania należy zastąpić je klasą stała 0 (lub odpowiednik typu wyliczeniowego go).|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|

