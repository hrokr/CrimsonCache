# CrimsonCache

CrimsonCache creates a synthetic blood bank database that matches the current aggregate blood donation data in the US. It’s designed for SQL practice.

# Immediate Start

If you're not interested in the generating your own database and just want something to practice on now, you can download just the databases by clicking the data folder above, then .sqlite3 files, and then `View raw` which should download it to your machine.

# About the data

CrimsonCache creates a synthetic dataset and, from that, a database. The people contained within it are not real; however, the aggregate statistics which the database models are. The sources of the statistics are [Statistica][1], an article by the [Stanford Blood Center][2], and [America's Blood Centers][3].

[Statistica][4] also provided data on changes amongst donors over time, including donations by race, and a breakdown of blood type and Rh by race for all but Native Americans and Hawaiian and Pacific Islanders. For these two groups, Rh breakdowns were approximated.  For Native Americans, a 93:7 percent split was used, based on the work of this [paper][5]. The Rh breakdown for Hawaiian and Pacific Islanders was approximated from the [Blood Bank of Hawaii][6]. The results were aggregated by blood type.

Regarding race, you’ll notice I have an unusual mix of color along with what is normally construed as race for field names, and all of which is now referred to as ethnicity. I don’t believe this the best way of capturing diversity, but I don’t think race works either. Caucasian and African-American are ethnicities, but one could be white with no ancestors from the Caucasus

Or you could be like an friend of mine who had immigrated from Egypt and whose ancestors had lived in Egypt for hundreds years. It really stuck with him that people didn't think of him as African-American when he knew he had emigrated from Africa a few years earlier. The same goes for South Africans. And I have never once seen a comprehensive list of what all the races are supposed to be or how how to be deal with how most people are mixed to some degree or another.

However, we know conditions like [sickle cell disease][7] have a genetic component that is best described with the accurate (but wordy) “people of sub-Saharan African origin living in other parts of the world,” so dispensing with the collection is probably not a great idea. And, I just found out that Peru is close to 100% O positive, and the Blackfoot Native American tribe is about 70% A positive.

So, I'm calling it ethnicity and that stays until it gets replaced by something better.

# About the schema

The schema is modified from [Blood Bank Management and Inventory Control Database Management System][8] by Aman Shah, et al. In the paper they propose a system and schema that would not likely work in the US (India has, as least notionally, universal health care; the US is mostly for profit). However, I don't think it's necessary to develop a schema that captures a fictional US blood bank *in excruciating detail* in order to create a functional dataset.

# Future Work

Right now this is what I need to focus on:

- [ ] Minor fixes
            - Have names match sex
- [ ] Statistical tests
- [ ] Outside validation
            - I'm not sure about the best way to do this. Ideally, it would be to get access to a real dataset
              but that may not be possible
- [ ] Test to ensure a seed produces a reproducible result
- [x] Export to database(s)
            - Ingest to SQLlite or Postgres. That allows for a follow-on project with ELT pipeline for analysis
- [ ] Refactor for hypothesis testing
            - The goal is to be able to model questions like "What happens if we have a successful program where
              people continue to donate?" or "If people are economically stressed and less likely to donate, how would impact supply?"
- [ ] Incorporating dynamic data to simulate changes in donation patterns over time in ways that are similar to but different from actual changes
- [ ] Add more detailed fake demographic information, such as age and location

[1]: https://www.statista.com/topics/7512/blood-donation-in-the-us/
[2]: https://stanfordbloodcenter.org/products-and-services/
[3]: https://americasblood.org/statistics_guide/
[4]: https://www.statista.com/statistics/1203831/blood-type-distribution-us-by-ethnicity/
[5]: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2135301/pdf/73.pdf
[6]: https://www.bbh.org/about-blood/
[7]: https://en.wikipedia.org/wiki/Sickle_cell_disease
[8]: https://pdf.sciencedirectassets.com/280203/1-s2.0-S1877050921X0021X/1-s2.0-S187705092102500X/main.pdf?X-Amz-Security-Token=IQoJb3JpZ2luX2VjEEsaCXVzLWVhc3QtMSJIMEYCIQCbPa%2FKD0yl%2FqfFXImAfHxvvJ10GkQZ4kU8Djp93OhI0QIhAM9FkMegvsdFiS9V7Os9RmY6DY1mxpMvBfi%2Bu3im4JxLKrwFCPT%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEQBRoMMDU5MDAzNTQ2ODY1Igz52eAhDo3%2BkWWpqkAqkAUvJeLo8rTB2vA7aYr%2F%2BbSOfmeMbM3piqMmBeuf5pz7eeTEIAw6ukFT8%2BxVQZzH8fFSdOYxpRchv67VBxl%2BK53F6PoFw%2FnkHDrceNW9gw60ra7kr13pMmlK1LyTlfQ3otk6keIhz1aNA3Yi0KfrWhdtbJ5abvF237t81XaqOa3H2t6ZnHj0uspSfXzKwClQ%2FHL132nADZj1mgRvkXT5sH8wQKdOHJu%2FQUPDR1oJyK2Esd%2BzLfzkjRDNoLlIWNbr2L1qIvSTEQ5RkvxU1eMgrKBr2J1LqTFzQt6ih95DBP531%2B3kqycsQSQRWdzuIfSeJP6Xye9KsZmctsIfC1YATBzL8uzknLNpVSiFwFoL54zblc30y9Ycue4KZ38WqxD2eOxj6jZgJv1xlQE%2FB6ozIP1ZE%2FU%2BOEYIKEnB9vwEEn46muXKalV2XSIGko33zI3jVIRbjMjC2FfDTf7tGTzjj4ptOBdfz%2BYWIpBkpugR%2Fdi5Na6rjcc3qMJr0%2BvQsJV611L9FiADH6DNQvbDM326GyCkjjB4NeqH5D0m8U7dS6uFb%2Ba4vhcr3BbmM1Wo1ClzYSz899QBpeS6gDUhYOTIKcZCRaIL5hsEzdnvns%2FyI1UJiWWb0lMMmLAoGZF%2BcIkao92rSJuSjGsnGcSeOJVJXXyJjlyKXFpecvAuDOxcXWkGMb%2B7WOanMEXzj1dh%2FpYi749ONO1QuI8Uihfes318VmTyKUxwoo%2FgNQkuV3BHPpDtExtDniYPhTM5wvRayLu3CqgOhlqusQspgOlw45yISRvX33R5%2BscgftptldU6ksB%2BxYKOchiZ%2FDWOfGXXgxMSNi1Fd%2BJINZoVpO4rV2BYSNzb2vcU94o4hhNUw446UaNP6jD84PazBjqwAdysiw9eiHLss7Un0elcb%2FF%2Ftvde1Y96Fix0lWz%2FLYanTRe7B%2BB%2BfNv3hGqJT1OLLgNUdpnw5IV5NynaE4NYpgNsTwRJGfUx2kGhQaRS5RGBHFyiiWeuBzS5sW1B1u8F6jpneSIdEk0bYA2Ffw0RDbiOZluKzocGV3DsL0UpUYszuxM04%2FVqAneghKMcj1p42KpSCIUynIJIPn6bRzyrySk4Z02%2BT1yb4GDRMey2yxD7&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20240627T192713Z&X-Amz-SignedHeaders=host&X-Amz-Expires=300&X-Amz-Credential=ASIAQ3PHCVTYR5RUENMT%2F20240627%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Signature=bfb2aa5fb529b983273e649463fc2b7d51e83f6318890809d61534cf33ee48f3&hash=1614cd609439309b59eb542a12c1f86cbfe8a743cec3ff97ac7f1dde70ce769b&host=68042c943591013ac2b2430a89b270f6af2c76d8dfd086a07176afe7c76c2c61&pii=S187705092102500X&tid=spdf-9aaf8be1-e624-4a65-9eda-ce7b95bec271&sid=31cac7c213efd943e58a47b4e8a2d377183cgxrqa&type=client&tsoh=d3d3LnNjaWVuY2VkaXJlY3QuY29t&ua=16165b5b06530b5457&rr=89a7d549a8473b38&cc=us
