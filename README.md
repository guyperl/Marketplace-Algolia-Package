[![](https://scdn.rapidapi.com/RapidAPI_banner.png)](https://rapidapi.com/package/Algolia/functions?utm_source=RapidAPIGitHub_AlgoliaFunctions&utm_medium=button&utm_content=RapidAPI_GitHub)

# Algolia Package
The Algolia API includes autocomplete functionality and an instant results display.
* Domain: [algolia.com](https://www.algolia.com/)
* Credentials: apiKey, appId

## How to get credentials:
1. Login into your [Algolia Dashboard](https://www.algolia.com/dashboard)
2. Go to API [Keys section](https://www.algolia.com/api-keys)
3. Use your Application ID as `appId` and Admin API Key as `apiKey`

## Custom datatypes:
 |Datatype|Description|Example
 |--------|-----------|----------
 |Datepicker|String which includes date and time|```2016-05-28 00:00:00```
 |Map|String which includes latitude and longitude coma separated|```50.37, 26.56```
 |List|Simple array|```["123", "sample"]```
 |Select|String with predefined values|```sample```
 |Array|Array of objects|```[{"Second name":"123","Age":"12","Photo":"sdf","Draft":"sdfsdf"},{"name":"adi","Second name":"bla","Age":"4","Photo":"asfserwe","Draft":"sdfsdf"}] ```

## Algolia.searchMultipleIndexes
This method allows to send multiple search queries, potentially targeting multiple indices, in a single API call.

| Field | Type       | Description
|-------|------------|----------
| apiKey| credentials| Algolia Application Key.
| appId | credentials| Algolia Application ID.
| requests| Array     | List of queries. Results will be received in the same order as the queries in the requests attribute. Each query is described by the following attributes: indexName: index targeted by the query; params: URL-encoded list of search parameters.
| strategy | credentials| Algolia Application ID.Allows optimizing execution of the queries by potentially skipping some of them. The following values are allowed: none: Execute all queries. stopIfEnoughMatches: Execute queries one by one, but stop as soon as one query matches at least as many hits as its hitsPerPage parameter. More formally: query N is executed only if all of queries 0 through N-1 had strictly less hits than their requested number of hits per page. Let’s illustrate stopIfEnoughMatches: Let’s say you send 3 queries with hitsPerPage set to 50, 5 and 20 (respectively). There are different possible scenarios: `Run query #1` 50+ hits are found: skip to step 4 otherwise: continue with query #2 `Run query #2` 5+ hits where found: skip to step 4 otherwise: continue with query #3 `Run query #3` This is the last query, so we don’t care about its outcome Return results `Return actual results` for queries that were processed Return empty hits for queries that were skipped, along with a processed attribute set to false.


## Algolia.getLogs
Return last logs.

| Field | Type       | Description
|-------|------------|----------
| apiKey| credentials| Algolia Application Key.
| appId | credentials| Algolia Application ID.
| offset| Number     | Specify the first entry to retrieve (0-based, 0 is the most recent log entry). Defaults to 0.
| length| Number     | Specify the maximum number of entries to retrieve starting at offset. Defaults to 10. Maximum allowed value: 1000.
| type  | Select     | Specify the type of logs to retrieve. This parameter is useful for debugging, especially when it is difficult to locate errors among many API calls:`all` (default): Retrieve all logs; `query`: Retrieve only the queries; `build`: Retrieve only the build operations; `error`: Retrieve only the errors
| indexName | String     | Index for which log entries should be retrieved. When omitted, log entries are retrieved across all indices.

## Algolia.addGlobalApiKey
This method add a new global API key.

| Field                 | Type       | Description
|-----------------------|------------|----------
| apiKey                | credentials| Algolia Application Key.
| appId                 | credentials| Algolia Application ID.
| validity              | Number     | Specify a validity for this key in seconds (the key will automatically be removed after this period of time). Defaults to 0 (no validity limit).
| maxQueriesPerIPPerHour| Number     | Specify the maximum number of API calls allowed from an IP address per hour.
| maxHitsPerQuery       | Number     | Specify the maximum number of hits this API key can retrieve in one call. Defaults to 0 (unlimited).
| acl                   | List       | Contains the list of rights for this key. Here is the complete list of ACL that can be used for a key: `search`, `browse`, `addObject`, `deleteObject`, `deleteIndex`, `settings`, `editSettings`, `analytics`, `listIndexes`
| indexes               | List       | Restrict this new API key to specific index names. This option is useful if you want to isolate your development and production environments: you can have one API key targeting all development indices and another one that target all production indices. You can target all indices starting by a prefix or finishing by a suffix with the ‘*’ character (for example "dev_*” matches all indices starting by "dev_” and "*_dev” matches all indices finishing by "_dev”). If the list is empty or not set, the API Key will be valid for all indices.
| referers              | List       | Restrict this new API key to specific referers. You can specify a pattern with one or two *. For example, "https://algolia.com/*” matches all referers starting with "https://algolia.com/” and "*algolia.com” matches all referers ending with ".algolia.com”. You can combine both of them to like "*.algolia.com*” to allow the domain algolia.com. Defaults to all referers if empty or blank
| queryParameters       | String     | Force some query parameters to be applied foreach query made with this api key. You can force all query parameters like: "typoTolerance=strict&ignorePlurals=false&filters=rights:public”. The parameters use the url string format.
| description           | String     | Used to identify a key.

#### `acl` example:
```json
"acl": ["search"]
```
#### `indexes` example:
```json
"indexes": ["dev_index"]
```
#### `referers` example:
```json
"referers": ["https://algolia.com/*"]
```

## Algolia.updateGlobalApiKey
This method update a global API key.

| Field                 | Type       | Description
|-----------------------|------------|----------
| apiKey                | credentials| Algolia Application Key.
| appId                 | credentials| Algolia Application ID.
| key                   | String     | Key to update
| validity              | Number     | Specify a validity for this key in seconds (the key will automatically be removed after this period of time). Defaults to 0 (no validity limit).
| maxQueriesPerIPPerHour| Number     | Specify the maximum number of API calls allowed from an IP address per hour.
| maxHitsPerQuery       | Number     | Specify the maximum number of hits this API key can retrieve in one call. Defaults to 0 (unlimited).
| acl                   | List       | Contains the list of rights for this key. Here is the complete list of ACL that can be used for a key: `search`, `browse`, `addObject`, `deleteObject`, `deleteIndex`, `settings`, `editSettings`, `analytics`, `listIndexes`
| indexes               | List       | Restrict this new API key to specific index names. This option is useful if you want to isolate your development and production environments: you can have one API key targeting all development indices and another one that target all production indices. You can target all indices starting by a prefix or finishing by a suffix with the ‘*’ character (for example "dev_*” matches all indices starting by "dev_” and "*_dev” matches all indices finishing by "_dev”). If the list is empty or not set, the API Key will be valid for all indices.
| referers              | List       | Restrict this new API key to specific referers. You can specify a pattern with one or two *. For example, "https://algolia.com/*” matches all referers starting with "https://algolia.com/” and "*algolia.com” matches all referers ending with ".algolia.com”. You can combine both of them to like "*.algolia.com*” to allow the domain algolia.com. Defaults to all referers if empty or blank
| queryParameters       | String     | Force some query parameters to be applied foreach query made with this api key. You can force all query parameters like: "typoTolerance=strict&ignorePlurals=false&filters=rights:public”. The parameters use the url string format.
| description           | String     | Used to identify a key.

#### `acl` example:
```json
"acl": ["search"]
```
#### `indexes` example:
```json
"indexes": ["dev_index"]
```
#### `referers` example:
```json
"referers": ["https://algolia.com/*"]
```

## Algolia.getGlobalApiKeys
This method Lists global API keys with their rights. These keys have been created with the add global key API.

| Field | Type       | Description
|-------|------------|----------
| apiKey| credentials| Algolia Application Key.
| appId | credentials| Algolia Application ID.

## Algolia.getGlobalApiKeyRights
This method returns the rights of a given global API key that has been created with the add global Key API.

| Field | Type       | Description
|-------|------------|----------
| apiKey| credentials| Algolia Application Key.
| appId | credentials| Algolia Application ID.
| key   | String     | Key to retrieve.

## Algolia.deleteGlobalApiKey
This method deletes a global API key that has been created with the add global Key API.

| Field | Type       | Description
|-------|------------|----------
| apiKey| credentials| Algolia Application Key.
| appId | credentials| Algolia Application ID.
| key   | String     | Key to be deleted

## Algolia.getSingleSynonymsSet
Fetch a single synonyms set, identified by the given `objectId`

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index name to retrieve single synonyms set for
| objectId     | String     | Object ID of synonyms set.

## Algolia.deleteSingleSynonymsSet
Delete a single synonyms set, identified by the given `objectId`

| Field          | Type       | Description
|----------------|------------|----------
| apiKey         | credentials| Algolia Application Key.
| appId          | credentials| Algolia Application ID.
| indexName      | String     | Index name to delete single synonyms set for
| objectId       | String     | Object ID of synonyms set.
| forwardToSlaves| Boolean    | Delete the synonyms set in all slave indices as well

## Algolia.deleteAllSynonyms
Delete all synonyms from the index

| Field          | Type       | Description
|----------------|------------|----------
| apiKey         | credentials| Algolia Application Key.
| appId          | credentials| Algolia Application ID.
| indexName      | String     | Index name to clear synonyms for
| forwardToSlaves| Boolean    | Delete the synonyms set in all slave indices as well

## Algolia.searchSynonyms
Search/browse all synonyms, possibly filtered by type

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index name to search synonyms for
| query        | String     | The query string used to search for specific synonyms. Use an empty string (default) to browse all synonyms.
| type         | List     | Only search within specific types of synonyms. Multiple types can be specified using a comma-separated list. Possible values: `synonym`, `onewaysynonym`, `altcorrection1`, `altcorrection2`, `placeholder`
| page         | String     | The page to fetch (first page is 0).
| hitsPerPage  | String     | The number of synonyms to fetch per page.

## Algolia.createRegularSynonymSet
Create a new regular synonym set

| Field         | Type       | Description
|---------------|------------|----------
| apiKey        | credentials| Algolia Application Key.
| appId         | credentials| Algolia Application ID.
| indexName     | String     | Index name.
| objectId      | String     | Object ID.
| forwardToSlave| Boolean    | Push the new/updated synonyms set to all slave indices
| synonyms      | List       | Array of synonym strings

#### `synonyms` example:
```json
"synonyms": [ "iphone", "ephone", "aphone", "yphone", "apple phone"]
```

## Algolia.updateRegularSynonymSet
Update a new regular synonym set

| Field         | Type       | Description
|---------------|------------|----------
| apiKey        | credentials| Algolia Application Key.
| appId         | credentials| Algolia Application ID.
| indexName     | String     | Index name.
| objectId      | String     | Object ID.
| forwardToSlave| Boolean    | Push the new/updated synonyms set to all slave indices
| synonyms      | List       | Array of synonym strings

#### `synonyms` example:
```json
"synonyms": [ "iphone", "ephone", "aphone", "yphone", "apple phone"]
```

## Algolia.createOnуWaySynonymSet
Create a new one-way synonym set

| Field         | Type       | Description
|---------------|------------|----------
| apiKey        | credentials| Algolia Application Key.
| appId         | credentials| Algolia Application ID.
| indexName     | String     | Index name.
| objectId      | String     | Object ID.
| forwardToSlave| Boolean    | Push the new/updated synonyms set to all slave indices
| input         | String     | Let’s take an example. When a user searches for "tablet”, you want them to be able to find iPads and Galaxy Note tablets alike, but you might not want Android tablets to show up when they search for "iPad”. To do this, you would create a one-way synonym record between tablet (as input) and ipad, galaxy note (as synonyms). When the user types in "tablet”, records containing "iPad” and "Galaxy Note” will be returned. However records containing only "tablet” or "Galaxy Note” won’t be returned if he searches for "iPad”.
| synonyms      | JSON       | Array of synonym strings

#### `synonyms` example:
```json
"synonyms": [ "ephone", "aphone", "yphone", "apple phone"]
```

## Algolia.updateOneWaySynonymSet
Update a new one-way synonym set

| Field         | Type       | Description
|---------------|------------|----------
| apiKey        | credentials| Algolia Application Key.
| appId         | credentials| Algolia Application ID.
| indexName     | String     | Index name.
| objectId      | String     | Object ID.
| forwardToSlave| Boolean    | Push the new/updated synonyms set to all slave indices
| input         | String     | Let’s take an example. When a user searches for "tablet”, you want them to be able to find iPads and Galaxy Note tablets alike, but you might not want Android tablets to show up when they search for "iPad”. To do this, you would create a one-way synonym record between tablet (as input) and ipad, galaxy note (as synonyms). When the user types in "tablet”, records containing "iPad” and "Galaxy Note” will be returned. However records containing only "tablet” or "Galaxy Note” won’t be returned if he searches for "iPad”.
| synonyms      | JSON       | Array of synonym strings
#### `synonyms` example:
```json
"synonyms": [ "ephone", "aphone", "yphone", "apple phone"]
```
## Algolia.createAlternativeCorrectionSynonymSet
Create a new alternative correction synonym set.
Alternative corrections are just like one-way synonyms, but they allow you to account for one or two typos when an alternative is matched, thus impacting the ranking of the matched records via the typo criterion in the ranking formula.

This construct can be used to make sure common misspellings are taken into account when they fall outside of the typo-tolerance rules, or when you want to take into account alternative words for a search term but with a lower ranking in the results.

To reuse the previous example, you could define tablet as input and ipad as synonym in the same way but with an alternative correction type.

The engine would then account for one or two typos for records containing "iPad” when the user types in "tablet”, thus giving priority in the results to records that actually contain the word "tablet”.

| Field         | Type       | Description
|---------------|------------|----------
| apiKey        | credentials| Algolia Application Key.
| appId         | credentials| Algolia Application ID.
| indexName     | String     | Index name.
| objectId      | String     | Object ID.
| forwardToSlave| Boolean    | Push the new/updated synonyms set to all slave indices
| type          | Select     | Valid values: `altcorrection1`, `altcorrection2`.
| word          | String     | Word to add alternative synonyms collection for
| corrections   | List       | Array of corrections strings. Example: `["ipad"]`

## Algolia.updateAlternativeCorrectionSynonymSet
Update a new alternative correction synonym set

| Field         | Type       | Description
|---------------|------------|----------
| apiKey        | credentials| Algolia Application Key.
| appId         | credentials| Algolia Application ID.
| indexName     | String     | Index name.
| objectId      | String     | Object ID.
| forwardToSlave| Boolean    | Push the new/updated synonyms set to all slave indices
| type          | Select     | Valid values: `altcorrection1`, `altcorrection2`.
| word          | String     | Word to add alternative synonyms collection for
| corrections   | List       | Array of corrections strings.

#### `correction` example:
```json
"corrections": [ "ephone", "aphone", "yphone", "apple phone"]
```

## Algolia.createPlaceholderSynonymSet
Create a new placeholder correction synonym set

| Field         | Type       | Description
|---------------|------------|----------
| apiKey        | credentials| Algolia Application Key.
| appId         | credentials| Algolia Application ID.
| indexName     | String     | Index name.
| objectId      | String     | Object ID.
| forwardToSlave| Boolean    | Push the new/updated synonyms set to all slave indices
| placeholder   | String     | Word to add placeholder collection for
| replacements  | List       | Array of replacements strings

#### `replacements` example:
```json
"replacements": [ "ephone", "iphone"]
```
## Algolia.updatePlaceholderSynonymSet
Update a new placeholder correction synonym set

| Field         | Type       | Description
|---------------|------------|----------
| apiKey        | credentials| Algolia Application Key.
| appId         | credentials| Algolia Application ID.
| indexName     | String     | Index name.
| objectId      | String     | Object ID.
| forwardToSlave| Boolean    | Push the new/updated synonyms set to all slave indices
| placeholder   | String     | Word to add placeholder collection for
| replacements  | List       | Array of replacements strings

#### `replacements` example:
```json
"replacements": [ "ephone", "iphone"]
```

## Algolia.getIndexes
This command lists all your existing indexes.

| Field | Type       | Description
|-------|------------|----------
| apiKey| credentials| Algolia Application Key.
| appId | credentials| Algolia Application ID.

## Algolia.querySingleIndex
Return objects that match the query.

| Field                           | Type       | Description
|---------------------------------|------------|----------
| apiKey                          | credentials| Algolia Application Key.
| appId                           | credentials| Algolia Application ID.
| indexName                       | String     | Inex name to retrieve.
| query                           | String     | The instant-search query string, all words of the query are interpreted as prefixes (for example "John Mc” will match "John Mccamey” and "Johnathan Mccamey”). If no query parameter is set, retrieves all objects.
| queryType                       | Select     | Selects how the query words are interpreted: `prefixAll`, `prefixLast`, `prefixNone`
| typoTolerance                   | Select     | This setting has four different options: `true` (default), `false`, `min`: keep only results with the lowest number of typo, `strict`: if there is a match without typo, then all results with 2 typos or more will be removed.
| minWordSizefor1Typo             | Number     | The minimum number of characters in a query word to accept one typo in this word. Defaults to 4.
| minWordSizefor2Typos            | Number     | The minimum number of characters in a query word to accept two typos in this word. Defaults to 8.
| allowTyposOnNumericTokens       | String     | If set to false, disable typo-tolerance on numeric tokens (=numbers) in the query word. For example the query `304` will match with `30450`, but not with `40450` that would have been the case with typo-tolerance enabled. Can be very useful on serial numbers and zip codes searches. Defaults to true.
| ignorePlurals                   | Boolean    | If set to true, simple plural forms won’t be considered as typos (for example car/cars will be considered as equal). Defaults to false.
| restrictSearchableAttributes    | String     | List of attributes you want to use for textual search
| advancedSyntax                  | String     | Enable the advanced query syntax. Defaults to 0 (false).
| analytics                       | Boolean    | If set to false, this query will not be taken into account for the Analytics. Defaults to true.
| analyticsTags                   | String     | Comma-separated string list. If set, tag your query with the specified identifiers. Tags can then be used in the Analytics to analyze a subset of searches only.
| replaceSynonymsInHighlight      | Boolean    | If set to false, words matched via synonyms expansion will not be replaced by the matched synonym in the highlighted result. Defaults to true.
| optionalWords                   | String     | Specify a list of words that should be considered as optional when found in the query. The list of words is comma separated. This list will be appended to the one defined in your index settings.
| minProximity                    | String     | Configure the precision of the `proximity` ranking criterion. By default, the minimum (and best) proximity value distance between 2 matching words is `1`. Setting it to `2` (or `3`) would allow 1 (or `2`) words to be found between the matching words without degrading the proximity ranking value. Considering the query "javascript framework”, if you set `minProximity=2` the records "JavaScript framework” and "JavaScript charting framework” will get the same proximity score, even if the second one contains a word between the 2 matching words. Defaults to 1. _Note_: the maximum minProximity that can be set is `7`. Above, the engine will consider the proximity rule from the rankignFormula as disabled.
| removeWordsIfNoResults          | String     | Configure the way query words are removed when the query doesn’t retrieve any results. Configure the way query words are removed when the query doesn’t retrieve any results. This option can be used to avoid having an empty result page. There are four different options: `lastWords`: when a query does not return any result, the last word will be added as optionalWords (the process is repeated with the n-1 word, n-2 word, … until there is results). This option is particularly useful on e-commerce websites `firstWords`: when a query does not return any result, the first word will be added as optionalWords (the process is repeated with the second word, third word, … until there is results). This option is useful on address search; `allOptional`: When a query does not return any result, a second trial will be made with all words as optional (which is equivalent to transforming the AND operand between query terms in a OR operand); `none`: No specific processing is done when a query does not return any result. (Defaults to `none`)
| disableTypoToleranceOnAttributes| String     | List of attributes on which you want to disable typo tolerance
| removeStopWords                 | String     | Remove stop words from query before executing it. It can be a boolean: enable or disable all 41 supported languages or a string array with the list of languages you have in your record (using language iso code).  In most use-cases, we don’t recommend enabling this option. List of 41 supported languages with their associated iso code: Arabic=ar, Armenian=hy, Basque=eu, Bengali=bn, Brazilian=pt-br, Bulgarian=bg, Catalan=ca, Chinese=zh, Czech=cs, Danish=da, Dutch=nl, English=en, Finnish=fi, French=fr, Galician=gl, German=de, Greek=el, Hindi=hi, Hungarian=hu, Indonesian=id, Irish=ga, Italian=it, Japanese=ja, Korean=ko, Kurdish=ku, Latvian=lv, Lithuanian=lt, Marathi=mr, Norwegian=no, Persian (Farsi)=fa, Polish=pl, Portugese=pt, Romanian=ro, Russian=ru, Slovak=sk, Spanish=es, Swedish=sv, Thai=th, Turkish=tr, Ukranian=uk, Urdu=ur
| exactOnSingleWordQuery          | String     | This parameter control how the exact ranking criterion is computed when the query contains one word. There is three different values: `none`, `word`, `attribute` (default)
| alternativesAsExact             | String     | Specify the list of approximation that should be considered as an exact match in the ranking formula:ignorePlurals: alternative word added by the ignore plurals feature singleWordSynonym: single word synonym (For example "NY” = "NYC”)multiWordsSynonym: synonym over multiple words (For example "NY” = "New York”). The default value is `ignorePlurals`, `singleWordSynonym`.
| page                            | Number     | Pagination parameter used to select the page to retrieve. Page is zero-based and defaults to 0. Thus, to retrieve the 10th page you need to set page=9
| hitsPerPage                     | Number     | Pagination parameter used to select the number of hits per page. Defaults to 20.
| offset                          | Number     | Specify the offset of the first hit to return.Instead of page/hitsPerPage, you can use offset/length to specify the number of hits you want to retrieve and from which offset you want to start.
| length                          | Number     | Set the number of hits to retrieve (used only with offset).Instead of page/hitsPerPage, you can use offset/length to specify the number of hits you want to retrieve and from which offset you want to start.
| attributesToRetrieve            | List     | List of object attributes you want to retrieve (let you minimize the answer size). List of object attributes you want to retrieve (let you minimize the answer size). Attributes are separated with a comma (for example "name,address" ), you can also use a JSON string array encoding (for example encodeURIComponent('["name","address"]') ). By default, all attributes are retrieved. You can also use * to retrieve all values when an attributesToRetrieve setting is specified for your index.
| attributesToHighlight           | String     | List of attributes you want to highlight according to the query. Attributes are separated by a comma. You can also use a JSON string array encoding (for example `encodeURIComponent('["name","address"]') )`. If an attribute has no match for the query, the raw value is returned. By default all indexed text attributes are highlighted. You can use * if you want to highlight all textual attributes. Numerical attributes are not highlighted. A matchLevel is returned for each highlighted attribute and can contain: `full`: if all the query terms were found in the attribute; `partial`: if only some of the query terms were found; `none`: if none of the query terms were found
| attributesToSnippet             | String     | List of attributes to snippet alongside the number of words to return (syntax is 'attributeName:nbWords').Attributes are separated by a comma (Example: `attributesToSnippet=name:10`, `content:10` ). You can also use a JSON string array encoding (Example: `encodeURIComponent('["name:10","content:10"]'` )) By default no snippet is computed.
| getRankingInfo                  | Number     | If set to 1, the result hits will contain ranking information in _rankingInfo attribute.
| highlightPreTag                 | String     | Specify the string that is inserted before the highlighted parts in the query result (defaults to `<em>`).
| highlightPostTag                | String     | Specify the string that is inserted after the highlighted parts in the query result (defaults to `</em>`
| snippetEllipsisText             | String     | String used as an ellipsis indicator when a snippet is truncated (defaults to empty).
| responseFields                  | String     | Choose which fields the response will contain. Applies to search and browse queries. By default, all fields are returned. If this parameter is specified, only the fields explicitly listed will be returned, unless * is used, in which case all fields are returned. Specifying an empty list or unknown field names is an error. This parameter is mainly intended to limit the response size. For example, for complex queries, echoing of request parameters in the response’s params field can be undesirable.
| numericFilters                  | String     | The list of numeric filters you want to apply separated by a comma. The syntax of one filter is `AttributeName` followed by Operator followed by Value . Supported operators are: `<` `<=` `=` `>` `>=` `!=`. You can easily perform range queries via the : operator (equivalent to combining >= and <= operators), for example numericFilters=price:10 to 1000. You can also mix OR and AND operators. The OR operator is defined with a parenthesis syntax. For example (`code=1 AND (price:[0-100] OR price:[1000-2000]))` translates in `encodeURIComponent("code=1,(price:0 to 10,price:1000 to 2000)`"). You can also use a JSON string array encoding. For example: `encodeURIComponent('["price>100","code=1"]')`
| tagFilters                      | String     | Filter the query by a set of tags. You can AND tags by separating them by commas. To OR tags, you must add parentheses. For example: tagFilters=`tag1,(tag2,tag3)` means tag1 AND (tag2 OR tag3) . At indexing, tags should be added in the _tags attribute of objects (for example: {"_tags":["tag1","tag2"]}). You can also use a JSON string array encoding, for example:`encodeURIComponent('["tag1",["tag2","tag3"]]')` means *tag1 AND (tag2 OR tag3) *. Negations are supported via the - operator, prefixing the value. For example: `tagFilters=tag1,-tag2`.
| distinct                        | Number     | Enable the distinct feature (disabled by default) if the attributeForDistinct index setting is set. This feature is similar to the SQL "distinct” keyword: when enabled in a query with the distinct=1 parameter, all hits containing a duplicate value for theattributeForDistinct attribute are removed from results. For example, if the chosen attribute is show_name and several hits have the same value for show_name, then only the best one is kept and others are removed.
| facets                          | String     | List of object attributes that you want to use for faceting. Attributes are separated with a comma (for example "category,author" ). You can also use a JSON string array encoding (for example encodeURIComponent('["category","author"]') ). Only attributes that have been added in attributesForFaceting index setting can be used in this parameter. You can also use* to perform faceting on all attributes specified in attributesForFaceting. If the number of results is important, the count can be approximate, the attribute exhaustiveFacetsCount in the response is true when the count is exact.
| facetFilters                    | String     | Filter the query by a list of facets. Facets are separated by commas and each facet is encoded as attributeName:value. To OR facets, you must add parentheses. For example: facetFilters=(category:Book,category:Movie),author:John%20Doe. You can also use a JSON string array encoding (for example: encodeURIComponent('[["category:Book","category:Movie"],"author:John Doe"]') ). Negations are supported via the - operator, prefixing the facet value. For example: encodeURIComponent('["category:Book","category:-Movie","author:John Doe"]').
| maxValuesPerFacet               | Number     | Limit the number of facet values returned for each facet. For example: maxValuesPerFacet=10 will retrieve max 10 values per facet. Defaults to 100.
| filters                         | String     | Filter the query with numeric, facet or/and tag filters. The syntax is a SQL like syntax, you can use the OR and AND keywords. The syntax for the underlying numeric, facet and tag filters is the same than in the other filters: `available=1` AND (category:Book OR NOT category:Ebook) AND _tags:public. `date`: 1441745506 TO 1441755506 AND `inStock` > 0 AND author:"John Doe". The list of keywords is: __OR__: create a disjunctive filter between two filters. __AND__: create a conjunctive filter between two filters. __TO__: used to specify a range for a numeric filter. __NOT__: used to negate a filter. The syntax with the ‘-‘ isn’t allowed.
| aroundLatLng                    | String     | Search for entries around a given latitude/longitude (specified as two floats separated by a comma, for example: aroundLatLng=47.316669,5.016670). You can specify the maximum distance in meters with the aroundRadius parameter but we recommend to let it unset and let our automatic radius computation adapt it depending of the density of the are. At indexing, you should specify the geo-location of an object with the _geoloc attribute (in the form "_geoloc":{"lat":48.853409, "lng":2.348800} or "_geoloc":[{"lat":48.853409, "lng":2.348800},{"lat":48.547456, "lng":2.972075}] if you have several geo-locations in your record).
| aroundRadius                    | String     | Control the radius associated with a aroundLatLng or aroundLatLngViaIP query.
| aroundPrecision                 | String     | Control the precision of a aroundLatLng query. In meter. For example if you set aroundPrecision=100, two objects that are in the range 0-99m will be considered as identical in the ranking for the .variable geo ranking parameter (same for 100-199, 200-299, … ranges).
| minimumAroundRadius             | String     | Define the minimum radius used for aroundLatLng or aroundLatLngViaIP when aroundRadius is not set. The radius is computed automatically using the density of the area. You can retrieve the computed radius in the automaticRadius attribute of the answer.
| insideBoundingBox               | String     | Search for entries inside a given area defined by the two extreme points of a rectangle (defined by 4 floats: p1Lat,p1Lng,p2Lat, p2Lng, for example: insideBoundingBox=47.3165,4.9665,47.3424,5.0201). At indexing, you should specify geoloc of an object with the _geoloc attribute (in the form "_geoloc":{"lat":48.853409, "lng":2.348800} or "_geoloc":[{"lat":48.853409, "lng":2.348800},{"lat":48.547456, "lng":2.972075}] if you have several geo-locations in your record).
| insidePolygon                   | String     | Search entries inside a given area defined by a set of points (defined by a minimum of 6 floats: p1Lat,p1Lng,p2Lat,p2Lng,p3Lat,p3Long). For example, "insidePolygon=47.3165, 4.9665, 47.3424, 5.0201, 47.32, 4.98"). At indexing, you should specify the geo location of an object with the _geoloc attribute (in the form "_geoloc":{"lat":48.853409, "lng":2.348800} or "_geoloc":[{"lat":48.853409, "lng":2.348800},{"lat":48.547456, "lng":2.972075}] if you have several geo-locations in your record)`. To make an UNION of multiple polygons, you can use this syntax: insidePolygon=[[42.01,-124.31, 42,-120.00 ,39.01,-120.00 ,35,-114.63], [46.01,-124.31, 42,-150.00 ,39.01,-120.00 ,35,-114.63]].
| optionalFilters     | List     | Create filters for ranking purposes, to rank higher records that contain the filter(s)
| sumOrFiltersScores      | Boolean     | Determines how to calculate the total score for filtering When sumOrFiltersScores is false, max score will be kept. When sumOrFiltersScores is true, score will be summed. False means that the total score of a record is the maximum score of an individual filter. Setting it to true changes the total score by adding together the scores of each filter found. For more on scoring, check out our filter scoring overview.(s)
| facetingAfterDistinct    | Boolean     | Force faceting to be applied after de-duplication. When using the distinct setting in combination with faceting, facet counts may be higher than expected. This is because the engine computes faceting before applying de-duplication (distinct). When facetingAfterDistinct is set to true, you force faceting to be computed after de-duplication has been applied.You should not use facetingAfterDistinct=true if you don’t have the same facet values in all records sharing the same distinct key (you would get inconsistent results). facetingAfterDistinct can only be set at query time; it can’t be added as a default setting of the index. facetingAfterDistinct will be ignored if you also set typoTolerance to either strict or min.
| sortFacetValuesBy    | String     | When using facets, Algolia retrieves a list of matching facet values for each faceted attribute. This parameter controls how the facet values are sorted within each faceted attribute. Supported options are: count (default): Facet values are sorted by decreasing count, the count being the number of records containing this facet value in the results of the query. alpha: Facet values are sorted by increasing alphabetical order.
| restrictHighlightAndSnippetArrays    | Boolean     | Restrict arrays in highlight and snippet results to items that matched the query. When false, all array items are highlighted/snippeted. When true, only array items that matched at least partially are highlighted/snippeted.
| aroundLatLngViaIP    | String     | Search for entries around a given location automatically computed from the requester’s IP address.
| disableExactOnAttributes    | String     | List of attributes on which you want to disable computation of the exact ranking criterion The list must be a subset of the searchableAttributes index setting. searchableAttributes must not be empty nor null for disableExactOnAttributes to be applied.
| enableRules    | Boolean     | Whether rules should be globally enabled. This is a global switch that affects all rules. When true, rules processing is enabled: rules may match the query. When false, rules processing is disabled: no rule will match the query.
| ruleContexts    | String     | Enables contextual rules. Provides a list of contexts for which rules are enabled. Contextual rules matching any of these contexts are eligible, as well as generic rules. When empty, only generic rules are eligible. For performance reasons, you may activate a maximum of 10 contexts at query time. (You may use an unlimited number of contexts in your rules.)
| maxFacetHits    | Number     | Maximum number of facet hits to return during a search for facet values. Does not apply to regular search queries. For performance reasons, the maximum allowed number of returned values is 100. Any value outside the range [1, 100] will be rejected.
| percentileComputation    | Boolean     | Whether to include the query in processing time percentile computation. When true, the API records the processing time of the search query and includes it when computing the 90% and 99% percentiles, available in your Algolia dashboard. When false, the search query is excluded from percentile computation.


## Algolia.deleteSingleIndex
This method deletes an existing index.

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index name to delete.

## Algolia.clearSingleIndex
This method deletes the index content. Settings and index specific API keys are kept untouched.

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index name to clear

## Algolia.addSingleObjectToIndex
This method adds one object in the index with automatic assignation of `objectId`.

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index name to add object for.
| object       | JSON       | Object body.

#### `object` format:
```json
{
	"name": "Betty Jane Mccamey",
	"company": "Vita Foods Inc.",
	"email": "betty@mccamey.com"
}
```

## Algolia.updateSingleObject
This method adds or replaces an object (if the object does not exist, it will be created). Be careful, when an object already exists for the specified object ID, the whole object is replaced: existing attributes that are not replaced are deleted.

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index name to add object for.
| objectId     | String     | Index name to add object for.
| object       | JSON       | Object body.

#### `object` format:
```json
{
	"name": "Betty Jane Mccamey",
	"company": "Vita Foods Inc.",
	"email": "betty@mccamey.com"
}
```

## Algolia.partiallyUpdateObject
This method updates part of an object (if the object does not exist, it will be created. You can avoid an automatic creation of the object by passing createIfNotExists=false as query argument).

| Field            | Type       | Description
|------------------|------------|----------
| apiKey           | credentials| Algolia Application Key.
| appId            | credentials| Algolia Application ID.
| indexName        | String     | Index name to add object for.
| objectId         | String     | Index name to add object for.
| object           | JSON       | Object body.
| createIfNotExists| Boolean    | You can avoid an automatic creation of the object. Defaults is `true`

#### `object` format:
```json
{
	"name": "Betty Jane Mccamey",
	"company": "Vita Foods Inc.",
	"email": "betty@mccamey.com"
}
```

## Algolia.batchObjectsWrite
Perform multiple write operations in a single API call.

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index name to add object for.
| requests       | JSON       | Request objects.

#### `requests` format:
```json
{"requests": [
    {
      "action": "addObject",
      "body": {
                "name": "Betty Jane Mccamey",
                "company": "Vita Foods Inc.",
                "email": "betty@mccamey.com"
              }
    },
    {
        "action": "updateObject",
        "objectID": "123",
        "body": {
                  "name": "Gayla Geimer",
                  "company": "Ortman Mccain Co",
                  "email": "gayla@geimer.com"
                }
      }
  ]
}
```
### following actions supported
```
addObject: Add an object. Equivalent to Add an object without ID.

updateObject: Add or replace an existing object. You must set the objectID attribute to indicate the object to update. Equivalent to Add/update an object by ID.

partialUpdateObject: Partially update an object. You must set the objectID attribute to indicate the object to update. Equivalent to Partially update an object.

partialUpdateObjectNoCreate: Same as partialUpdateObject, except that the object is not created if the object designed by objectID does not exist.

deleteObject: Delete an object. You must set the objectID attribute to indicate the object to delete. Equivalent to Delete an object.

delete: Delete the index. Equivalent to Delete an index.

clear: Remove the index’s content, but keep settings and index-specific API keys untouched. Equivalent to Clear an index.
```


## Algolia.getSingleObject
This method returns one object from the index.

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index name to add object for.
| objectId     | String     | Index name to add object for.
| attributes     | List     | List of attributes to retrieve. If not specified, all retrievable attributes are returned.

## Algolia.getObjects
This method allows to retrieve several objects with one API call.

| Field       | Type       | Description
|-------------|------------|----------
| apiKey      | credentials| Algolia Application Key.
| appId       | credentials| Algolia Application ID.
| requests    | Array       | JSON Array of Objects.

#### `requests` format
```json
[
	{ "indexName": "index1", "objectID": "obj1","attributesToRetrieve":["objectID"] },
	{ "indexName": "index1", "objectID": "obj2","attributesToRetrieve":["objectID"] }
]
```

## Algolia.deleteSingleObject
This method deletes an existing object from the index

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index name to delete.
| objectId     | String     | Index name to delete.

## Algolia.getIndexSettings
This method retrieve index settings.

| Field                           | Type       | Description
|---------------------------------|------------|----------
| apiKey                          | credentials| Algolia Application Key.
| appId                           | credentials| Algolia Application ID.
| indexName                       | String     | Index name to retrieve settings for.

## Algolia.getIndexContent
This method allows you to retrieve all index content (for backup, SEO or analytics purpose). It can retrieve up to 1,000 records per call and supports full text search and filters.

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index name to retrieve content for.
| params    | String     | Search parameters used to filter the index content. If not specified, all objects are returned. Can only be used on the first call.
| cursor    | String     | Cursor indicating the location to resume browsing from. Must match the value returned by the previous call.

## Algolia.changeIndexSettings
This method updates part of index settings, the list of attributes and their behavior are listed in the get index settings API.

| Field                           | Type       | Description
|---------------------------------|------------|----------
| apiKey                          | credentials| Algolia Application Key.
| appId                           | credentials| Algolia Application ID.
| indexName                       | String     | Index name to retrieve settings for.
| forwardToSlaves                 | Boolean    | If this parameter is true, the change is also applied on slaves of this index.
| attributesToIndex               | List       | JSON Array of Strings. The list of fields you want to index. If set to null, all textual attributes of your objects are indexed, but you should update it to get optimal results.
| numericAttributesToIndex        | String     | All numerical attributes are automatically indexed as numerical filters. If you don’t need filtering on some of your numerical attributes, please consider sending them as strings to speed up the indexing. If you only need to filter on a numeric value with the operator = or !=, you can speed up the indexing by specifying the attribute with equalOnly(AttributeName). The other operators will be disabled.
| attributesForFaceting           | List       | The list of fields you want to use for faceting. All strings in the attribute selected for faceting are extracted and added as a facet. By default, no attribute is used for faceting.
| attributeForDistinct            | String     | The attribute name used for the Distinct feature. This feature is similar to the SQL "distinct” keyword: when enabled in query with the distinct=1 parameter, all hits containing a duplicate value for this attribute are removed from results. For example, if the chosen attribute is show_name and several hits have the same value for show_name, then only the best one is kept and others are removed.
| ranking                         | JSON       | JSON Array of Strings. Controls the way results are sorted.
| customRanking                   | List       | JSON Array of Strings. Lets you specify part of the ranking. The syntax of this condition is an array of strings containing attributes prefixed by asc (ascending order) or desc (descending order) operator. For example: `customRanking`: [`desc(population)`, `asc(name)`]
| separatorsToIndex               | String     | Specify the separators (punctuation characters) to index. By default, separators are not indexed. Use `+#` to be able to search Google+ or C#.
| slaves                          | String     | JSON Array of String. The list of indexes on which you want to replicate all write operations. In order to get response times in milliseconds, we pre-compute part of the ranking during indexing. If you want to use different ranking configurations depending of the use-case, you need to create one index per ranking configuration. This option enables you to perform write operations only on this index, and to automatically update slave indexes with the same operations.
| unretrievableAttributes         | String     | JSON Array Of Strings. List of attributes that cannot be retrieved at query time. This feature allows you to have an attribute that is used for indexing and/or ranking but which cannot be retrieved. This setting will be bypassed if the query is done with the ADMIN API key. Defaults to null.
| allowCompressionOfIntegerArray  | Boolean    | Allows compression of big integer arrays. We recommended to store the list of user ID or rights as an integer array and enable this setting. When enabled the integer array are reordered to reach a better compression ratio. Defaults to false.
| synonyms                        | JSON       | JSON Array Of Strings. An array of array of string considered as equal. See README for more info
| placeholders                    | JSON       | JSON Hash. This is an advanced use case to define a token substitutable by a list of words without having the original token searchable.
| altCorrections                  | JSON       | Specify alternative corrections that you want to consider.
| disableTypoToleranceOnWords     | JSON       | JSON Array of String. Specify a list of words on which the automatic typo tolerance will be disabled.
| disableTypoToleranceOnAttributes| JSON       | JSON Array of Strings. List of attributes on which you want to disable typo tolerance (must be a subset of the attributesToIndex index setting). By default the list is empty.
| disablePrefixOnAttributes       | JSON       | List of attributes on which you want to disable prefix matching
| disableExactOnAttributes        | JSON       | JSON Array of String. List of attributes on which you want to disable the computation of "exact” criteria (must be a subset of the attributesToIndex index setting). By default the list is empty.
| minWordSizefor1Typo             | Number     | The minimum number of characters to accept one typo (default = 4).
| minWordSizefor2Typos            | Number     | The minimum number of characters to accept two typos (default = 8).
| hitsPerPage                     | Number     | The number of hits per page (default = 10).
| attributesToRetrieve            | JSON       | JSON Array of String. Default list of attributes to retrieve in objects. If set to null, all attributes are retrieved.
| attributesToHighlight           | JSON       | JSON Array of String. Default list of attributes to highlight. If set to null, all indexed attributes are highlighted.
| attributesToSnippet             | JSON       | JSON Array of Strings. Default list of attributes to snippet alongside the number of words to return (syntax is ‘attributeName:nbWords’). If set to null, no snippet is computed.
| queryType                       | String     | Select how the query words are interpreted, it can be one of the following value: `prefixAll`, `prefixLast`, `prefixNone`.
| minProximity                    | Number     | Configure the precision of the proximity ranking criterion.
| highlightPreTag                 | String     | Specify the string that is inserted before the highlighted parts in the query result (defaults to `&lt;em&gt;`).
| highlightPostTag                | String     | Specify the string that is inserted after the highlighted parts in the query result (defaults to `&lt;/em&gt;`).
| optionalWords                   | JSON       | JSON Array of Strings. Specify a list of words that should be considered as optional when found in the query
| allowTyposOnNumericTokens       | Boolean    | If set to false, disable typo-tolerance on numeric tokens (=numbers) in the query word. For example the query `304` will match with `30450`, but not with `40450` that would have been the case with typo-tolerance enabled. Can be very useful on serial numbers and zip codes searches. Defaults to false.
| ignorePlurals                   | Boolean    | If set to true, simple plural forms won’t be considered as typos (for example car/cars will be considered as equal). Defaults to false.
| advancedSyntax                  | Boolean    | Enable the advanced query syntax. Defaults to 0 (false).
| replaceSynonymsInHighlight      | Boolean    | If set to false, words matched via synonyms expansion will not be replaced by the matched synonym in the highlighted result. Defaults to true.
| maxValuesPerFacet               | Number     | Limit the number of facet values returned for each facet. For example: maxValuesPerFacet=10 will retrieve max 10 values per facet. Defaults to 100.
| distinct                        | Number     | Enable the distinct feature (disabled by default) if the attributeForDistinct index setting is set. This feature is similar to the SQL "distinct” keyword: when enabled in a query with the distinct=1 parameter, all hits containing a duplicate value for theattributeForDistinct attribute are removed from results. For example, if the chosen attribute is show_name and several hits have the same value for show_name, then only the best one is kept and others are removed.
| typoTolerance                   | Select     | This setting has four different options: `true`, `false`, `min`, `strict`.
| removeStopWords                 | String     | Remove stop words from query before executing it. It can be a boolean: enable or disable all 41 supported languages or a comma separated string with the list of languages you have in your record (using language iso code). In most use-cases, we don’t recommend enabling this option. List of 41 supported languages with their associated iso code: Arabic=ar, Armenian=hy, Basque=eu, Bengali=bn, Brazilian=pt-br, Bulgarian=bg, Catalan=ca, Chinese=zh, Czech=cs, Danish=da, Dutch=nl, English=en, Finnish=fi, French=fr, Galician=gl, German=de, Greek=el, Hindi=hi, Hungarian=hu, Indonesian=id, Irish=ga, Italian=it, Japanese=ja, Korean=ko, Kurdish=ku, Latvian=lv, Lithuanian=lt, Marathi=mr, Norwegian=no, Persian (Farsi)=fa, Polish=pl, Portugese=pt, Romanian=ro, Russian=ru, Slovak=sk, Spanish=es, Swedish=sv, Thai=th, Turkish=tr, Ukranian=uk, Urdu=ur. Stop words removal is applied on query words that are not interpreted as a prefix. The behavior depends of the queryType parameter: * queryType=prefixLast means the last query word is a prefix and it won’t be considered for stop words removal' * queryType=prefixNone means no query word are prefix, stop words removal will be applied on all query words' * queryType=prefixAll means all query terms are prefix, stop words won’t be removed. This parameter is useful when you have a query in natural language like “what is a record?”. In this case, before executing the query, we will remove “what”, “is” and “a” in order to just search for “record”. This removal will remove false positive because of stop words, especially when combined with optional words. For most use cases, it is better to do not use this feature as people search by keywords on search engines.
| snippetEllipsisText             | String     | String used as an ellipsis indicator when a snippet is truncated. Default: `…` (U+2026 HORIZONTAL ELLIPSIS).
| exactOnSingleWordQuery          | String     | This parameter control how the exact ranking criterion is computed when the query contains one word. There is three different values: `none`, `word`, `attribute`.
| alternativesAsExact             | String     | Specify the list of approximation that should be considered as an exact match in the ranking formula.
| sortFacetValuesBy    | String     | When using facets, Algolia retrieves a list of matching facet values for each faceted attribute. This parameter controls how the facet values are sorted within each faceted attribute. Supported options are: count (default): Facet values are sorted by decreasing count, the count being the number of records containing this facet value in the results of the query. alpha: Facet values are sorted by increasing alphabetical order.
| restrictHighlightAndSnippetArrays    | Boolean     | Restrict arrays in highlight and snippet results to items that matched the query. When false, all array items are highlighted/snippeted. When true, only array items that matched at least partially are highlighted/snippeted.
| paginationLimitedTo  | Number     | Set the maximum number of hits accessible via pagination. This can be set at indexing time, to define a default. The index value can also be overidden at query time. By default, this parameter is set to 1000 to guarantee good performance. We recommend keeping the default value to guarantee excellent performance. Increasing the pagination limit will have a direct impact on the performance of search queries. A too high value will also make it very easy for anyone to retrieve (“scrape”) your entire dataset.
| removeWordsIfNoResults          | String     | Configure the way query words are removed when the query doesn’t retrieve any results. Configure the way query words are removed when the query doesn’t retrieve any results. This option can be used to avoid having an empty result page. There are four different options: `lastWords`: when a query does not return any result, the last word will be added as optionalWords (the process is repeated with the n-1 word, n-2 word, … until there is results). This option is particularly useful on e-commerce websites `firstWords`: when a query does not return any result, the first word will be added as optionalWords (the process is repeated with the second word, third word, … until there is results). This option is useful on address search; `allOptional`: When a query does not return any result, a second trial will be made with all words as optional (which is equivalent to transforming the AND operand between query terms in a OR operand); `none`: No specific processing is done when a query does not return any result. (Defaults to `none`)
| enableRules    | Boolean     | Whether rules should be globally enabled. This is a global switch that affects all rules. When true, rules processing is enabled: rules may match the query. When false, rules processing is disabled: no rule will match the query.
| responseFields                  | String     | Choose which fields the response will contain. Applies to search and browse queries. By default, all fields are returned. If this parameter is specified, only the fields explicitly listed will be returned, unless * is used, in which case all fields are returned. Specifying an empty list or unknown field names is an error. This parameter is mainly intended to limit the response size. For example, for complex queries, echoing of request parameters in the response’s params field can be undesirable.
| maxFacetHits    | Number     | Maximum number of facet hits to return during a search for facet values. Does not apply to regular search queries. For performance reasons, the maximum allowed number of returned values is 100. Any value outside the range [1, 100] will be rejected.
| camelCaseAttributes       | String | List of attributes on which to do a decomposition of camel case words. Camel case compounds are basically words glued together, and being able to find a camel case compound when searching for one of its words often makes sense. This setting automatically splits camel case compounds into separate words and allows for example to find "camelCaseAttributes" when searching for "case".

#### `attributesToIndex` example:
```json
"attributesToIndex": ["title,alternative_title", "text"]`
```

#### `attributesForFaceting` example:
```json
"attributesForFaceting": ["filterOnly(attributeName)"]
```
#### `ranking` example:
```json
"ranking": ["typo", "geo", "words", "custom"]
```
#### `customRanking` example:
```json
"customRanking": ["desc(population)", "asc(name)"]
```
#### `synonyms` example:
```json
"synonyms": [ [ "black", "dark" ], [ "small", "little", "mini" ], ... ]
```

#### `placeholders` example:
```json
"placeholders": { "<name>" : ["placeholder2","placeholder1"] }
```

#### `altCorrections` example:
```json
"altCorrections": [
	{ "word" : "foot", "correction": "feet", "nbTypos": 1},
	{ "word": "feet", "correction": "foot", "nbTypos": 1}
]
```

#### `disableTypoToleranceOnWords` example:
```json
"disableTypoToleranceOnWords": ["word2", "word1"]`
```

#### `disableTypoToleranceOnAttributes`, `disablePrefixOnAttributes`, `disableExactOnAttributes`, `attributesToHighlight`, `attributesToSnippet`, `attributesToRetrieve`, `attributesToHighlight`, `attributesToSnippet` example:
```json
"...": ["attr1", "attr2"]`
```

#### `optionalWords` example:
```json
"optionalWords": ["word2", "word1"]`
```

#### `alternativesAsExact` example:
```json
"alternativesAsExact": ["ignorePlurals", "singleWordSynonym", ]
```

## Algolia.copySingleIndex
This method copy an existing index. If the destination index already exists, its specific API keys will be preserved and the source index specific API keys will be added.

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index name to move
| destination  | String     | Specify the name of the destination index

## Algolia.moveSingleIndex
This method move an existing index. If the destination index already exists, its specific API keys will be preserved and the source index specific API keys will be added.

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index name to move
| destination  | String     | Specify the name of the destination index

## Algolia.getTaskStatus
This method gets the status of a given task (published or notPublished). Returns also a pendingTask flag that indicates if the index has remaining task(s) running.

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index name.
| task         | String     | Task to retrieve status for.

## Algolia.addIndexSpecificApiKey
This method add a new key that can access to this index.

| Field          | Type       | Description
|----------------|------------|----------
| apiKey         | credentials| Algolia Application Key.
| appId          | credentials| Algolia Application ID.
| indexName      | String     | Used to identify a key.
| description    | String     | Used to identify a key.
| acl            | List       | that can be used for a key: **search**: allow to search; **browse**: allow to retrieve all index content via the browse API; **addObject**: allows to add/update an object in the index (copy/move index are also allowed with this right)'; **deleteObject**: allows to delete an existing object; **deleteIndex**: allows to delete or clear index content; **settings**: allows to get index settings; **editSettings**: allows to change index settings; **analytics**: allows to retrieve the analytics through the analytics API. ; **listIndexes**: allows to list all accessible indexes
| referers       | List       | JSON Array of String. Restrict this new API key to specific referers. You can specify a pattern with one or two *. For example, "https://algolia.com/*” matches all referers starting with "https://algolia.com/” and "*.algolia.com” matches all referers ending with ".algolia.com”. You can combine both of them to like "*algolia.com*” to allow the domain algolia.com. Defaults to all referers if empty or blank
| queryParameters| String     | Force some query parameters to be applied foreach query made with this api key. You can force all query parameters like: "typoTolerance=strict&ignorePlurals=false&filters=rights:public”. The parameters use the url string format.
| validity       | Number     | Specify a validity for this key in seconds (the key will automatically be removed after this period of time). Defaults to 0 (no validity limit).
| maxHitsPerQuery| Number     | Specify the maximum number of hits this API key can retrieve in one call. Defaults to 0 (unlimited). This parameter can be used to protect you from attempts at retrieving your entire content by massively querying the index.

#### `acl` example:
```json
"acl": ["search", "browse"]
```
#### `referers` example:
```json
"referers": ["*.algolia.com”"]
```

## Algolia.updateIndexSpecificApiKey
This method update a key that can access to this index.

| Field          | Type       | Description
|----------------|------------|----------
| apiKey         | credentials| Algolia Application Key.
| appId          | credentials| Algolia Application ID.
| key            | String     | Key to update
| indexName      | String     | Used to identify a key.
| description    | String     | Used to identify a key.
| acl            | List       | that can be used for a key: **search**: allow to search; **browse**: allow to retrieve all index content via the browse API; **addObject**: allows to add/update an object in the index (copy/move index are also allowed with this right); **deleteObject**: allows to delete an existing object; **deleteIndex**: allows to delete or clear index content; **settings**: allows to get index settings; **editSettings**: allows to change index settings; **analytics**: allows to retrieve the analytics through the analytics API. ; **listIndexes**: allows to list all accessible indexes
| referers| List       | JSON Array of String. Restrict this new API key to specific referers. You can specify a pattern with one or two *. For example, "https://algolia.com/*” matches all referers starting with "https://algolia.com/” and "*.algolia.com” matches all referers ending with ".algolia.com”. You can combine both of them to like "*algolia.com*” to allow the domain algolia.com. Defaults to all referers if empty or blank
| queryParameters| String     | Force some query parameters to be applied foreach query made with this api key. You can force all query parameters like: "typoTolerance=strict&ignorePlurals=false&filters=rights:public”. The parameters use the url string format.
| validity       | Number     | Specify a validity for this key in seconds (the key will automatically be removed after this period of time). Defaults to 0 (no validity limit).
| maxHitsPerQuery| Number     | Specify the maximum number of hits this API key can retrieve in one call. Defaults to 0 (unlimited). This parameter can be used to protect you from attempts at retrieving your entire content by massively querying the index.

#### `acl` example:
```json
"acl": ["search", "browse"]
```
#### `referers` example:
```json
"referers": ["*.algolia.com”"]
```

## Algolia.getIndexSpecificApiKeys
This method Lists API keys that have access to this index with their rights. These keys have been created with the add index specific key API.

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index Name to list keys for.

## Algolia.getIndexApiKeysForAllIndexes
This method update a key that can access to this index.

| Field | Type       | Description
|-------|------------|----------
| apiKey| credentials| Algolia Application Key.
| appId | credentials| Algolia Application ID.

## Algolia.getIndexSpecificApiKeyRights
This method returns the rights of a given index specific API key that has been created with the add index specific key API.

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index name.
| key          | String     | Key to retrieve.

## Algolia.deleteIndexSpecificApiKey
This method delete an index specific API key that have been created with the add index specific key API.

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index name.
| key          | String     | Key to delete.

## Algolia.searchFacetValues
This method searches for values of a given facet, optionally restricting the returned values to those contained in objects matching other search criteria.

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index Name
| facetName    | String     | Facet Name
| params       | String     | params (string): Search parameters. You must specify at least the facetQuery parameter, which contains the text that will be searched inside the facet's values. You may also specify any number of other regular search parameters. They will apply to objects in the index.

#### `params` example:
```json
"params": "facetQuery=${facetQuery}"
```
## Algolia.deleteRecordByQuery
Delete all records matching the query.This endpoint doesn’t support all the options of a query, only its filters (numeric, facet, or tag) and geo queries. It also doesn’t accept empty filters or query.

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index name.
| params          | String     | Delete query.Example:facetFilters=category:test.

## Algolia.batchWriteOperations
Perform multiple write operations, potentially targeting multiple indices, in a single API call. This is essentially a multi-index version of Batch write operations. It can be useful to modify multiple indices at the same time (e.g. if you have one index per user).

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| requests          | Array     | List of operations to batch. Each operation is described by: indexName (string): name of the index targeted by this operation action (string): type of operation body (object): arguments to the operation (depends on the type of the operation).

#### Example
```
{
  "requests": [
    {
      "action": "addObject",
      "indexName": "contacts",
      "body": {
                "name": "Betty Jane Mccamey",
                "company": "Vita Foods Inc.",
                "email": "betty@mccamey.com"
              }
    },
    {
        "action": "addObject",
        "indexName": "public_contacts",
        "body": {
                  "name": "Gayla Geimer",
                  "company": "Ortman Mccain Co",
                  "email": "gayla@geimer.com"
                }
      }
  ]
}
```

## Algolia.batchSynonymsWriteOperations
Create/update multiple synonym objects at once, potentially replacing the entire list of synonyms if replaceExistingSynonyms is true. You should always use replaceExistingSynonyms to atomically replace all your synonyms on a production index. This is the only way to ensure your index always has a list of synonyms to use during the indexing of the new list.

| Field        | Type       | Description
|--------------|------------|----------
| apiKey       | credentials| Algolia Application Key.
| appId        | credentials| Algolia Application ID.
| indexName    | String     | Index name.
| requests          | Array     | List of operations to batch. The POST body must be a JSON array of synonym objects. The syntax of each object is the same as in Create/update a synonym. See more [here](https://www.algolia.com/doc/rest-api/search/#createupdate-a-synonym)

### Example 
```
  {
    "objectID": "2",
    "type": "onewaysynonym",
    "input": "iphone",
    "synonyms": [ "ephone", "aphone", "yphone", "apple phone"]
  }
```